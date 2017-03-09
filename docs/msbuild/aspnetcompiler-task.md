---
title: "AspNetCompiler Task | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#AspNetCompiler"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "MSBuild, AspNetCompiler task"
  - "AspNetCompiler task [MSBuild]"
ms.assetid: f811c019-a67b-4d54-82e6-e29549496f6e
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# AspNetCompiler Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

`AspNetCompiler` タスクは、aspnet\_compiler.exe をラップするものです。aspnet\_compiler.exe は、[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] アプリケーションをプリコンパイルするためのユーティリティです。  
  
## タスク パラメーター  
 `AspNetCompiler` タスクのパラメーターの説明を次の表に示します。  
  
|パラメーター|Description|  
|------------|-----------------|  
|`AllowPartiallyTrustedCallers`|省略可能な `Boolean` 型のパラメーターです。<br /><br /> このパラメーターに `true` を設定すると、厳密な名前のアセンブリで部分的に信頼された呼び出し元を使用できるようになります。|  
|`Clean`|省略可能な `Boolean` 型のパラメーターです。<br /><br /> このパラメーターに `true` を設定すると、プリコンパイル対象のアプリケーションはクリーン ビルドされます。  コンパイル済みのコンポーネントは、すべて再コンパイルされます。  既定値 `false` です。  このパラメーターは、aspnet\_compiler.exe の **\-c** スイッチに相当します。|  
|`Debug`|省略可能な `Boolean` 型のパラメーターです。<br /><br /> このパタメータに `true` を設定すると、コンパイル時にデバッグ情報 \(.pdb ファイル\) が出力されます。  既定値 `false` です。  このパラメーターは、aspnet\_compiler.exe の **\-d** スイッチに相当します。|  
|`DelaySign`|省略可能な `Boolean` 型のパラメーターです。<br /><br /> このパラメーターに `true` を設定すると、アセンブリは作成時に完全には署名されません。|  
|`FixedNames`|省略可能な `Boolean` 型のパラメーターです。<br /><br /> このパラメーターに `true` を設定すると、コンパイルされたアセンブリに固定名が付けられます。|  
|`Force`|省略可能な `Boolean` 型のパラメーターです。<br /><br /> このパラメーターに `true` を設定すると、ターゲット ディレクトリが既に存在する場合にターゲット ディレクトリが上書きされます。  既存のコンテンツは失われます。  既定値 `false` です。  このパラメーターは、aspnet\_compiler.exe の **\-f** スイッチに相当します。|  
|`KeyContainer`|省略可能な `String` 型のパラメーターです。<br /><br /> 厳密名キー コンテナーを指定します。|  
|`KeyFile`|省略可能な `String` 型のパラメーターです。<br /><br /> 厳密名キー ファイルの物理パスを指定します。|  
|`MetabasePath`|省略可能な `String` 型のパラメーターです。<br /><br /> アプリケーションの IIS メタベースの完全パスを指定します。  このパラメーターを `VirtualPath` パラメーターや `PhysicalPath` パラメーターと一緒に使用することはできません。  このパラメーターは、aspnet\_compiler.exe の **\-m** スイッチに相当します。|  
|`PhysicalPath`|省略可能な `String` 型のパラメーターです。<br /><br /> コンパイル対象のアプリケーションの物理パスを指定します。  このパラメーターを指定しなかった場合には、IIS メタベースを使用してアプリケーションの場所が判断されます。  このパラメーターは、aspnet\_compiler.exe の **\-p** スイッチに相当します。|  
|`TargetFrameworkMoniker`|省略可能な `String` 型のパラメーターです。<br /><br /> 使用する aspnet\_compiler.exe の .NET Framework のバージョンを示す TargetFrameworkMoniker を指定します。  .NET Framework のモニカーのみ使用できます。|  
|`TargetPath`|省略可能な `String` 型のパラメーターです。<br /><br /> コンパイルしたアプリケーションを格納するパスを物理パスで指定します。  指定しなかった場合、アプリケーションは、所定の場所にプリコンパイルされます。|  
|`Updateable`|省略可能な `Boolean` 型のパラメーターです。<br /><br /> このパラメーターに `true` を設定すると、プリコンパイル対象のアプリケーションは更新可能になります。  既定値 `false` です。  このパラメーターは、aspnet\_compiler.exe の **\-u** スイッチに相当します。|  
|`VirtualPath`|省略可能な `String` 型のパラメーターです。<br /><br /> コンパイル対象のアプリケーションの仮想パスです。  `PhysicalPath` を指定した場合には、物理パスがアプリケーションの場所として使用されます。  指定しない場合には、IIS メタベースが使用され、アプリケーションは既定の場所に存在すると仮定されます。  このパラメーターは、aspnet\_compiler.exe の **\-v** スイッチに相当します。|  
  
## 解説  
 上記のパラメーター以外に、このタスクは <xref:Microsoft.Build.Tasks.ToolTaskExtension> クラスからパラメーターを継承します。このクラス自体は、<xref:Microsoft.Build.Utilities.ToolTask> クラスから継承されます。  これらの追加のパラメーターの一覧とその説明については、「[ToolTaskExtension Base Class](../msbuild/tooltaskextension-base-class.md)」を参照してください。  
  
## 使用例  
 `AspNetCompiler` タスクを使用して、[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] アプリケーションをプリコンパイルするコード例を次に示します。  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="PrecompileWeb">  
        <AspNetCompiler  
            VirtualPath="/MyWebSite"  
            PhysicalPath="c:\inetpub\wwwroot\MyWebSite\"  
            TargetPath="c:\precompiledweb\MyWebSite\"  
            Force="true"  
            Debug="true"  
        />  
    </Target>  
</Project>  
```  
  
## 参照  
 [タスク](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)