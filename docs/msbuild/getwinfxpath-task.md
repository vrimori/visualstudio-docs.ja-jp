---
title: "GetWinFXPath タスク | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- getting the directory of the current .NET Framework runtime [WPF MSBuild]
- GetWinFXPath task [WPF MSBuild], parameters
- GetWinFXPath task [WPF MSBuild]
- obtaining the path to the current .NET Framework runtime [WPF MSBuild]
ms.assetid: b1dfb467-f3d3-47f3-83ef-af7b0e33a772
caps.latest.revision: 5
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 79460291e91f0659df0a4241e17616e55187a0e2
ms.openlocfilehash: 45d07bf0834aa1488e8c2e3b22ee460eb629539e
ms.lasthandoff: 02/22/2017

---
# <a name="getwinfxpath-task"></a>GetWinFXPath タスク
<xref:Microsoft.Build.Tasks.Windows.GetWinFXPath> タスクは、現在の [!INCLUDE[TLA#tla_winfx](../msbuild/includes/tlasharptla_winfx_md.md)] ランタイムのディレクトリを返します。  
  
## <a name="task-parameters"></a>タスク パラメーター  
  
|パラメーター|説明|  
|---------------|-----------------|  
|`WinFXPath`|省略可能な **String** 型の出力パラメーターです。<br /><br /> [!INCLUDE[TLA2#tla_winfx](../msbuild/includes/tla2sharptla_winfx_md.md)] ランタイムへの実際のパスを指定します。|  
|`WinFXNativePath`|必須の **String** 型のパラメーターです。<br /><br /> ネイティブ [!INCLUDE[TLA2#tla_titlewinfx](../msbuild/includes/tla2sharptla_titlewinfx_md.md)] ランタイムへのパスを指定します。|  
|`WinFXWowPath`|必須の **String** 型のパラメーターです。<br /><br /> 64 ビット システムの 32 ビット **Windows on Windows** モジュール内の [!INCLUDE[TLA#tla_winfx](../msbuild/includes/tlasharptla_winfx_md.md)] アセンブリへのパスを指定します。|  
  
## <a name="remarks"></a>コメント  
 <xref:Microsoft.Build.Tasks.Windows.GetWinFXPath> タスクが 64 ビット プロセッサで実行されている場合は、**WinFXPath** パラメーターは **WinFXWowPath** パラメーターに保存されているパスに設定されます。それ以外の場合は、**WinFXPath** パラメーターは **WinFXNativePath** パラメーターに保存されているパスに設定されます。  
  
## <a name="example"></a>例  
 次の例では、**GetWinFXPath** タスクを使用して、[!INCLUDE[TLA2#tla_titlewinfx](../msbuild/includes/tla2sharptla_titlewinfx_md.md)] ランタイムへのネイティブ パスを検出する方法を示します。  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <UsingTask   
    TaskName="Microsoft.Build.Tasks.Windows.GetWinFXPath"   
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />  
  <Target Name="GetWinFXPathTask">  
    <GetWinFXPath  
      WinFXNativePath="c:\WinFXNative"   
      WinFXWowPath="c:\WinFXWowNative" />  
  </Target>  
  <Import Project="$(MSBuildBinPath)\Microsoft.WinFX.targets" />  
</Project>  
```  
  
## <a name="see-also"></a>関連項目  
 [WPF MSBuild リファレンス](../msbuild/wpf-msbuild-reference.md)   
 [Task Reference (タスク リファレンス)](../msbuild/wpf-msbuild-task-reference.md)   
 [MSBuild リファレンス](../msbuild/msbuild-reference.md)   
 [Task Reference (タスク リファレンス)](../msbuild/msbuild-task-reference.md)   
 [WPF アプリケーション (WPF) のビルド](http://msdn.microsoft.com/Library/a58696fd-bdad-4b55-9759-136dfdf8b91c)
