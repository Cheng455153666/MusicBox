source 'https://cdn.cocoapods.org/'

workspace './MusicBox.xcworkspace'
project './MusicBox/MusicBox.xcodeproj'

platform :ios, '14.0'
use_frameworks!

# ignore all warnings from all dependencies
inhibit_all_warnings!

def dev_pods
  pod 'SwiftLint', '= 0.43.1', configurations: ['Debug']
  # pod 'SwiftGen', '= 6.4.0', configurations: ['Debug']
  pod 'R.swift', '~> 5.4.0', configurations: ['Debug']
end

def core_pods
  pod 'RxSwift', '= 6.2.0'
  pod 'RxRelay', '= 6.2.0'
  pod 'Alamofire', '= 5.4.3'
end

def thirdparty_pods
  pod 'Firebase/Analytics', '= 8.4.0'
  pod 'Firebase/Crashlytics', '= 8.4.0'
  pod 'Firebase/RemoteConfig', '= 8.4.0'
  pod 'Firebase/Performance', '= 8.4.0'
end

def ui_pods
  pod 'SnapKit', '= 5.0.1'
  pod 'Kingfisher', '= 6.3.0'
  pod 'RxCocoa', '= 6.2.0'
  pod 'RxDataSources', '= 5.0.0'
  pod 'lottie-ios', '~> 3.2.3'
end

def test_pods
  pod 'Quick', '= 4.0.0'
  pod 'Nimble', '= 9.2.0'
  pod 'RxTest', '= 6.2.0'
  pod 'RxBlocking', '= 6.2.0'
end

target 'MusicBox' do
  dev_pods
  core_pods
  thirdparty_pods
  ui_pods
#  internal_pods
end

# target 'MusicBox Tests' do
#   core_pods
#   thirdparty_pods
#   test_pods
# end

post_install do |installer|
  installer.pods_project.targets.each do |target|
    target.build_configurations.each do |config|
      config.build_settings.delete 'IPHONEOS_DEPLOYMENT_TARGET'
      config.build_settings["EXCLUDED_ARCHS[sdk=iphonesimulator*]"] = "arm64"
    end
  end
end
