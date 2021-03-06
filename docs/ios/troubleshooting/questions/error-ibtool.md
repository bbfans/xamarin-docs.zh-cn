---
title: IBTool 错误： 无法完成该操作。
ms.topic: troubleshooting
ms.prod: xamarin
ms.assetid: A804EBC4-2BBF-4A98-A4E8-A455DB2E8A17
ms.technology: xamarin-ios
author: bradumbaugh
ms.author: brumbaug
ms.openlocfilehash: 4647227ad208bfa968f8282a966220a09ab7f4a6
ms.sourcegitcommit: 945df041e2180cb20af08b83cc703ecd1aedc6b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/04/2018
---
# <a name="ibtool-error-the-operation-couldnt-be-completed"></a>IBTool 错误： 无法完成该操作。

## <a name="fixed-in-xcode-611"></a>在 Xcode 6.1.1 中固定

Apple[固定](https://developer.apple.com/library/content/documentation/Xcode/Conceptual/RN-Xcode-Archive/Chapters/xc6_release_notes.html#//apple_ref/doc/uid/TP40016994-CH4-SW1)这`ibtool`在 Xcode 6.1.1，因此升级到 Xcode 6.1.1 或更高版本中的 bug 是最简单的修复程序。

* * *

## <a name="description-of-the-problem"></a>该问题的说明

`ibtool` Xcode 6.0 中的命令在 OS X 10.10 Yosemite 上有 bug。 Xamarin.iOS 使用 Xcode 的`ibtool`编译情节提要和`XIB`文件。

有关与 Xcode 相关错误的详细信息可以找到对以下堆栈溢出文章： [http://stackoverflow.com/questions/25754763/cant-open-storyboard](http://stackoverflow.com/questions/25754763/cant-open-storyboard)

### <a name="error-message"></a>错误消息

> 无法打开"MainStoryboard.storyboard"文档。 无法完成该操作。 （com.apple.InterfaceBuilder 错误-1）。

## <a name="workarounds-for-xcode-60"></a>解决方法 （对于 Xcode 6.0)

### <a name="option-1-manage-all-uiimageviewimage-properties-in-code"></a>选项 1： 管理所有`UIImageView.Image`代码中的属性

而不是设置`Image`属性`UIImageView`在情节提要或`.xib`文件，你可以在设置属性一个视图的视图控制器中的生命周期重写方法 (例如，在`ViewDidLoad()`)。 另请参阅[处理映像](~/ios/app-fundamentals/images-icons/index.md)有关使用提示和技巧`UIImage.FromBundle()`与`UIImage.FromFile()`。

### <a name="option-2-move-all-of-the-image-resources-to-the-top-level-resources-folder"></a>选项 2： 将所有图像资源移到顶级`Resources`文件夹

移到顶级的映像之后`Resources`文件夹中，你将需要更新情节提要和`.xib`文件以使用新的映像路径。

### <a name="option-3-set-the-logicalname-for-any-problematic-image-assets-so-they-are-copied-to-the-top-level-of-theapp-bundle"></a>选项 3： 设置`LogicalName`为任何有问题的图像资产，以便它们复制到的最高级别`.app`捆绑

例如，假设你原始`.csproj`文件包含以下条目：

`<BundleResource Include="Resources\Images\image.png" />`

你可以更改此元素，然后添加`LogicalName`以便图像将改为复制到的最高级别`.app `捆绑包：

```xml
<BundleResource Include="Resources\Images\image.png">
    <LogicalName>image.png</LogicalName>
</BundleResource>
```

Visual Studio 中用于 Mac`LogicalName`还可以通过使用设置`Resource ID`字段下面的图像**视图 > 填充 > 属性**。 (另请参阅： [ http://stackoverflow.com/questions/16938250/xamarin-studio-folder-structure-issue-in-ios-project/16951545#16951545 ](http://stackoverflow.com/questions/16938250/xamarin-studio-folder-structure-issue-in-ios-project/16951545#16951545))

此更改之后, 你将需要更新情节提要和`.xib`文件以使用新的顶级映像路径。 适用于 Mac 的 visual Studio 将自动更新为 autocompletions 列表`Image`iOS 设计器中的属性。 在 Visual Studio 中，你将需要手动编辑路径。 IOS 设计器将然后此应用显示为缺少的图像，但该项目将生成并运行正确。

### <a name="next-steps"></a>后续步骤

有关进一步的帮助，请与我们联系，或如果此问题仍然存在即使利用的上述信息，请参阅[哪些支持选项均可用于 Xamarin？](~/cross-platform/troubleshooting/support-options.md)有关联系人选项，建议的信息以及如何如果需要的文件的新 bug。 

