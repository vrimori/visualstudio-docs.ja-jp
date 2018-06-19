---
title: GetWinFXPath タスク | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e02d0f93dd406df170de2d4e83023fedced7d932
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
ms.locfileid: "31573445"
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
 <xref:Microsoft.Build.Tasks.Windows.GetWinFXPath> タスクが 64 ビット プロセッサで実行されている場合、**WinFXPath** パラメーターは **WinFXWowPath** パラメーターに保存されているパスに設定されます。それ以外の場合、**WinFXPath** パラメーターは **WinFXNativePath** パラメーターに保存されているパスに設定されます。  
  
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
  
## <a name="see-also"></a>参照  
 [WPF MSBuild リファレンス](../msbuild/wpf-msbuild-reference.md)   
 [Task Reference (タスク リファレンス)](../msbuild/wpf-msbuild-task-reference.md)   
 [MSBuild リファレンス](../msbuild/msbuild-reference.md)   
 [Task Reference (タスク リファレンス)](../msbuild/msbuild-task-reference.md)   
 [WPF アプリケーション (WPF) のビルド](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)