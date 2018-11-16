---
title: LC タスク | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#LC
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, LC task
- LC task [MSBuild]
ms.assetid: d5a53472-6f2a-42b8-a6db-593ca99c9790
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9f265e06deab522c0b994f0892fb6a96c7ac4a7f
ms.sourcegitcommit: 20d1b9a5bf041bb28453501eb63bc0537a8e4f54
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/14/2018
ms.locfileid: "51645056"
---
# <a name="lc-task"></a>LC タスク
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
LC.exe をラップします。LC.exe は .licx ファイルから .license ファイルを生成します。 LC.exe の詳細については、「[Lc.exe (ライセンス コンパイラ)](http://msdn.microsoft.com/library/2de803b8-495e-4982-b209-19a72aba0460)」を参照してください。  
  
## <a name="parameters"></a>パラメーター  
 `LC` タスクのパラメーターの説明を次の表に示します。  
  
|パラメーター|説明|  
|---------------|-----------------|  
|`LicenseTarget`|必須の <xref:Microsoft.Build.Framework.ITaskItem> 型のパラメーターです。<br /><br /> .licenses ファイルを生成する実行可能ファイルを指定します。|  
|`NoLogo`|省略可能な `Boolean` 型のパラメーターです。<br /><br /> Microsoft 著作権情報を表示しません。|  
|`OutputDirectory`|省略可能な `String` 型のパラメーターです。<br /><br /> 出力 .licenses ファイルを格納するディレクトリを指定します。|  
|`OutputLicense`|省略可能な <xref:Microsoft.Build.Framework.ITaskItem> 型の出力パラメーターです。<br /><br /> .licenses ファイルの名前を指定します。 名前を指定しなかった場合には、.licx ファイルの名前が使用され、.licenses ファイルは、.licx ファイルが格納されているディレクトリに作成されます。|  
|`ReferencedAssemblies`|省略可能な <xref:Microsoft.Build.Framework.ITaskItem>`[]` 型のパラメーターです。<br /><br /> .license ファイルの生成時に読み込む参照コンポーネントを指定します。|  
|`SdkToolsPath`|省略可能な `String` 型のパラメーターです。<br /><br /> resgen.exe などの SDK ツールのパスを指定します。|  
|`Sources`|必須の <xref:Microsoft.Build.Framework.ITaskItem>`[]` 型のパラメーターです。<br /><br /> .licenses ファイルに組み込むライセンス付きコンポーネントを格納するアイテムを指定します。 詳細については、「[Lc.exe (ライセンス コンパイラ)](http://msdn.microsoft.com/library/2de803b8-495e-4982-b209-19a72aba0460)」にある `/complist` スイッチの説明を参照してください。|  
  
 上記のパラメーター以外に、このタスクは <xref:Microsoft.Build.Tasks.ToolTaskExtension> クラスからパラメーターを継承します。このクラス自体は、<xref:Microsoft.Build.Utilities.ToolTask> クラスから継承されます。 これらの追加のパラメーターの一覧とその説明については、「[ToolTaskExtension 基本クラス](../msbuild/tooltaskextension-base-class.md)」を参照してください。  
  
## <a name="example"></a>例  
 `LC` タスクを使用してライセンスをコンパイルする例を次に示します。  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
<!-- Item declarations, etc -->  
  
    <Target Name="CompileLicenses">  
        <LC  
            Sources="@(LicxFile)"  
            LicenseTarget="$(TargetFileName)"  
            OutputDirectory="$(IntermediateOutputPath)"  
            OutputLicenses="$(IntermediateOutputPath)$(TargetFileName).licenses"  
            ReferencedAssemblies="@(ReferencePath);@(ReferenceDependencyPaths)">  
  
            <Output  
                TaskParameter="OutputLicenses"  
                ItemName="CompiledLicenseFile"/>  
        </LC>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>関連項目  
 [タスク](../msbuild/msbuild-tasks.md)   
 [Task Reference (タスク リファレンス)](../msbuild/msbuild-task-reference.md)



