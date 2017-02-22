---
title: "ResolveComReference Task | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#ResolveComReference"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "MSBuild, ResolveCOMReference task"
  - "ResolveCOMReference task [MSBuild]"
ms.assetid: c9bf5fcf-6453-40ea-b50f-a212adc3e9b5
caps.latest.revision: 26
caps.handback.revision: 26
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# ResolveComReference Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

1 つ以上のタイプ ライブラリ名または .tlb ファイルから成る一覧を使用して、これらのタイプ ライブラリのディスク上の位置を解決します。  
  
## パラメーター  
 `ResolveCOMReference` タスクのパラメーターの説明を次の表に示します。  
  
|パラメーター|説明|  
|------------|--------|  
|`DelaySign`|省略可能な `Boolean` 型のパラメーターです。<br /><br /> `true` に設定すると、アセンブリに公開キーが格納されます。  `false` に設定すると、アセンブリに完全な署名が行われます。|  
|`EnvironmentVariables`|省略可能な `String[]` 型のパラメーターです。<br /><br /> 等号で区切られた環境変数のペアの配列です。  これらの変数は、標準の環境ブロックに加え \(または標準の環境ブロックを選択的にオーバーライドして\)、子の tlbimp.exe と aximp.exe に渡されます。|  
|`ExecuteAsTool`|省略可能な `Boolean` 型のパラメーターです。<br /><br /> `true` の場合、アウトプロセスで適切なターゲット フレームワークの tlbimp.exe および aximp.exe が実行されて、必要なラッパー アセンブリが生成されます。  このパラメーターにより、マルチ ターゲットが可能になります。|  
|`IncludeVersionInInteropName`|省略可能な `Boolean` 型のパラメーターです。<br /><br /> `true` の場合、ラッパー名に typelib のバージョンが含まれるようになります。  既定値は `false` です。|  
|`KeyContainer`|省略可能な `String` 型のパラメーターです。<br /><br /> 公開キーと秘密キーのペアを保持するコンテナーを<br /><br /> 指定します。|  
|`KeyFile`|省略可能な `String` 型のパラメーターです。<br /><br /> 公開キーと秘密キーのペアを格納する項目を<br /><br /> 指定します。|  
|`NoClassMembers`|省略可能な `Boolean` 型のパラメーターです。|  
|`ResolvedAssemblyReferences`|省略可能な <xref:Microsoft.Build.Framework.ITaskItem>`[]` 型の出力パラメーター。<br /><br /> 解決されたアセンブリ参照を指定します。|  
|`ResolvedFiles`|省略可能な <xref:Microsoft.Build.Framework.ITaskItem>`[]` 型の出力パラメーター。<br /><br /> このタスクの入力として指定されたタイプ ライブラリについて、その物理的な位置に対応するディスク上の完全修飾ファイルを指定します。|  
|`ResolvedModules`|省略可能な <xref:Microsoft.Build.Framework.ITaskItem>`[]` 型のパラメーターです。|  
|`SdkToolsPath`|省略可能な [String](assetId:///String?qualifyHint=False&autoUpgrade=True) 型のパラメーターです。<br /><br /> `ExecuteAsTool` が `true` の場合、このパラメーターをターゲット フレームワークのバージョンに対応する SDK ツールのパスに設定する必要があります。|  
|`StateFile`|省略可能な assetId:///String?qualifyHint=False&autoUpgrade=True 型のパラメーターです。<br /><br /> COM コンポーネントのタイムスタンプのキャッシュ ファイルを指定します。  存在しない場合は、実行時に毎回すべてのラッパーが再生成されます。|  
|`TargetFrameworkVersion`|省略可能な assetId:///String?qualifyHint=False&autoUpgrade=True 型のパラメーターです。<br /><br /> プロジェクトのターゲット フレームワークのバージョンを指定します。<br /><br /> 既定値は `String.Empty` です。  これは、ターゲット フレームワークに基づく参照に対するフィルター処理が存在しないことを意味します。|  
|`TargetProcessorArchitecture`|省略可能な assetId:///String?qualifyHint=False&autoUpgrade=True 型のパラメーターです。<br /><br /> 優先されるターゲット プロセッサ アーキテクチャを指定します。  これは、変換後に tlbimp.exe\/machine フラグに渡されます。<br /><br /> パラメーター値は、<xref:Microsoft.Build.Utilities.ProcessorArchitecture> のメンバーである必要があります。|  
|`TypeLibFiles`|省略可能な <xref:Microsoft.Build.Framework.ITaskItem>`[]` 型のパラメーターです。<br /><br /> COM 参照に対するタイプ ライブラリ ファイル パスを指定します。  このパラメーターに含まれる項目には、項目メタデータが含まれることがあります。  詳細については、後述する「TypeLibFiles 項目 メタデータ」を参照してください。|  
|`TypeLibNames`|省略可能な <xref:Microsoft.Build.Framework.ITaskItem>`[]` 型のパラメーターです。<br /><br /> 解決するタイプ ライブラリ名を指定します。  このパラメーターに含まれる項目には、項目メタデータを含める必要があります。  詳細については、後述する「TypeLibNames 項目メタデータ」を参照してください。|  
|`WrapperOutputDirectory`|省略可能な `String` 型のパラメーターです。<br /><br /> 生成された相互運用機能アセンブリが格納される、ディスク上の場所。  この項目メタデータが指定されていない場合、タスクではプロジェクト ファイルの存在するディレクトリの絶対パスを使用します。|  
  
## 解説  
  
## TypeLibNames 項目メタデータ  
 `TypeLibNames` パラメーターに渡される項目で利用できる項目メタデータの説明を次の表に示します。  
  
|メタデータ|説明|  
|-----------|--------|  
|`GUID`|必須項目メタデータ。<br /><br /> タイプ ライブラリの GUID。  この項目メタデータが指定されていない場合、タスクは失敗します。|  
|`VersionMajor`|必須項目メタデータ。<br /><br /> タイプ ライブラリのメジャー バージョン。  この項目メタデータが指定されていない場合、タスクは失敗します。|  
|`VersionMinor`|必須項目メタデータ。<br /><br /> タイプ ライブラリのマイナー バージョン。  この項目メタデータが指定されていない場合、タスクは失敗します。|  
|`LocaleIdentifier`|省略可能な項目メタデータ。<br /><br /> タイプ ライブラリのロケール識別子 \(LCID\)。  32 ビット値で指定され、ユーザー、地域、またはアプリケーションで優先される言語を表します。  この項目メタデータが指定されていない場合、タスクでは既定のロケール識別子 "0" が使用されます。|  
|`WrapperTool`|省略可能な項目メタデータ。<br /><br /> このタイプ ライブラリのアセンブリ ラッパーを生成するためのラッパー ツールを指定します。  この項目メタデータが指定されていない場合、タスクでは既定のラッパー ツール "tlbimp" が使用されます。  利用できる typelib \(大文字と小文字を区別しない\) は次のとおりです。<br /><br /> -   `Primary`: COM コンポーネントの既に生成されたプライマリ相互運用機能アセンブリを使用する場合は、このラッパー ツールを使用します。  このラッパー ツールを使用するときは、ラッパー出力ディレクトリを指定しないでください。指定すると、タスクは失敗します。<br />-   `TLBImp`: COM コンポーネントの相互運用機能アセンブリを生成する場合は、このラッパー ツールを使用します。<br />-   `AXImp`: ActiveXコントロールの相互運用機能アセンブリを生成するには、このラッパー ツールを使用します。|  
  
## TypeLibFiles 項目メタデータ  
 `TypeLibFiles` パラメーターに渡される項目で利用できる項目メタデータの説明を次の表に示します。  
  
|メタデータ|説明|  
|-----------|--------|  
|`WrapperTool`|省略可能な項目メタデータ。<br /><br /> このタイプ ライブラリのアセンブリ ラッパーを生成するためのラッパー ツールを指定します。  この項目メタデータが指定されていない場合、タスクでは既定のラッパー ツール "tlbimp" が使用されます。  利用できる typelib \(大文字と小文字を区別しない\) は次のとおりです。<br /><br /> -   `Primary`: COM コンポーネントの既に生成されたプライマリ相互運用機能アセンブリを使用する場合は、このラッパー ツールを使用します。  このラッパー ツールを使用するときは、ラッパー出力ディレクトリを指定しないでください。指定すると、タスクは失敗します。<br />-   `TLBImp`: COM コンポーネントの相互運用機能アセンブリを生成する場合は、このラッパー ツールを使用します。<br />-   `AXImp`: ActiveXコントロールの相互運用機能アセンブリを生成するには、このラッパー ツールを使用します。|  
  
> [!NOTE]
>  タイプ ライブラリを一意に識別するための情報が増えると、タスクがディスク上の正しいファイルを解決できる可能性が高くなります。  
  
## 解説  
 上記のパラメーター以外に、このタスクは <xref:Microsoft.Build.Utilities.Task> クラスからパラメーターを継承します。  これらの追加のパラメーターの一覧とその説明については、「[Task Base Class](../msbuild/task-base-class.md)」を参照してください。  
  
## 参照  
 [タスク](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)