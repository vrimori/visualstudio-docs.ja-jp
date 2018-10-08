---
title: UidManager タスク | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- UidManager task [WPF MSBuild]
- UidManager task [WPF MSBuild], parameters
- managing UIDs when localizing XAML elements [WPF MSBuild]
- localizing XAML elements [WPF MSBuild], managing UIDs
- checking UIDs when localizing XAML elements [WPF MSBuild]
ms.assetid: 4fc7b5a5-11b0-46ca-9656-8c2a0b08d1fe
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8f64a91ddf1eea2bdd74bd64e2d33acfd4d60827
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47537107"
---
# <a name="uidmanager-task"></a>UidManager タスク
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[UidManager タスク](https://docs.microsoft.com/visualstudio/msbuild/uidmanager-task)します。  
  
  
<xref:Microsoft.Build.Tasks.Windows.UidManager> タスクでは、ソース [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] ファイルに含まれるすべての [!INCLUDE[TLA#tla_xaml](../includes/tlasharptla-xaml-md.md)] 要素をローカライズするために、一意識別子 (UID) をチェック、更新、または削除します。  
  
## <a name="task-parameters"></a>タスク パラメーター  
  
|パラメーター|説明|  
|---------------|-----------------|  
|`IntermediateDirectory`|省略可能な **String** 型のパラメーターです。<br /><br /> **MarkupFiles** パラメーターで指定されるソース [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] ファイルをバックアップするために使用されるディレクトリを指定します。|  
|`MarkupFiles`|必須の **ITaskItem[]** 型のパラメーターです。<br /><br /> UID のチェック、更新、または削除の対象となるソース [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] ファイルを指定します。|  
|`Task`|必須の **String** 型のパラメーターです。<br /><br /> 実行する UID 管理タスクを指定します。 有効なオプションは **Check**、**Update**、または **Remove** です。|  
  
## <a name="example"></a>例  
 次の例では <xref:Microsoft.Build.Tasks.Windows.UidManager> タスクを使用して、指定されたソース [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] ファイルに、適切な UID を持つ [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] 要素が含まれていることをチェックします。  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <UsingTask   
    TaskName="Microsoft.Build.Tasks.Windows.UidManager"   
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />  
  <Target Name="UidManagerTask">  
    <UidManager  
      Task="Check"  
      MarkupFiles="Page1.xaml;Page2.xaml"  
      IntermediateDirectory="c:\UidManagerIntermediateDirectory" />  
  </Target>  
</Project>  
```  
  
## <a name="see-also"></a>関連項目  
 [WPF MSBuild リファレンス](../msbuild/wpf-msbuild-reference.md)   
 [Task Reference (タスク リファレンス)](../msbuild/wpf-msbuild-task-reference.md)   
 [MSBuild リファレンス](../msbuild/msbuild-reference.md)   
 [Task Reference (タスク リファレンス)](../msbuild/msbuild-task-reference.md)   
 [WPF アプリケーション (WPF) のビルド](http://msdn.microsoft.com/library/a58696fd-bdad-4b55-9759-136dfdf8b91c)   
 [方法 : アプリケーションをローカライズする](http://msdn.microsoft.com/library/5001227e-9326-48a4-9dcd-ba1b89ee6653)



