# cocoapods与github
* github上传代码
    * 使用sourceTree
* cocoapods结合
    * pod spec create ZHWtools （创建.podspec文件），配置如下内容
    
```
Pod::Spec.new do |s|
  s.name         = "QFTimeUtil" # 项目名称
  s.version      = "0.0.1"        # 版本号 与 你仓库的 标签号 对应
  s.license      = "MIT"          # 开源证书
  s.summary      = "时间工具" # 项目简介

  s.homepage     = "https://github.com/sFeiYu/QFTimeUtil/tree/0.0.1" # 仓库的主页
  s.source       = { :git => "https://github.com/sFeiYu/QFTimeUtil.git", :tag => "#{s.version}" }#你的仓库地址，不能用SSH地址
  s.source_files = "TimeUtil/*.{h,m}" # 你代码的位置， BYPhoneNumTF/*.{h,m} 表示 BYPhoneNumTF 文件夹下所有的.h和.m文件
  s.requires_arc = true # 是否启用ARC
  s.platform     = :ios, "7.0" #平台及支持的最低版本
  # s.frameworks   = "UIKit", "Foundation" #支持的框架
  # s.dependency   = "AFNetworking" # 依赖库
  
  # User
  s.author             = { "sFeiYu" => "1208126673@qq.com" } # 作者信息
  #s.social_media_url   = "http://qiubaiying.github.io" # 个人主页

end
```
* pod lib lint ZHWtools.podspec（进行验证，只要没有error就行）
* pod trunk push ZHWtools.podspec（trunk push代码到cocoapods）
    * **注意：版本要和.podspec的版本一样**
* pod search ZHWtools （查找是否上传成功）
    
```
Authentication token is invalid or unverified. Either verify it with the email that was sent or register a new session
出现此错误时，
pod trunk register XXX@163.com XXXX
这个错误是因为你没有打开邮箱中发给你的网址，如果想重新发送请执行下面代码
```
* 如果搜索不到
 rm ~/Library/Caches/CocoaPods/search_index.json
