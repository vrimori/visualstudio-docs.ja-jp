---
title: "CreatePkgDef ユーティリティ | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "パッケージの定義"
  - "pkgdef を作成します。"
  - "pkgdef"
  - "createpkgdef"
ms.assetid: c745cb76-47a6-49ff-9eed-16af0f748e35
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# CreatePkgDef ユーティリティ
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

パラメーターとして Visual Studio 拡張機能の .dll ファイルは、.dll ファイルに付属する .pkgdef ファイルを作成します。 .Pkgdef ファイルには、拡張機能がインストールされている場合、システム レジストリに書き込むそれ以外の場合は、すべての情報が含まれています。  
  
> [!NOTE]
>  自動的に Visual Studio SDK に含まれているプロジェクト テンプレートのほとんどは、ビルド プロセスの一環として、.pkgdef ファイルを作成します。 このドキュメントはパッケージを手動で作成または .pkgdef 配置を使用する既存のパッケージを変換に必要な方を対象としています。  
  
## 構文  
  
```  
CreatePkgDef /out=FileName [/codebase] [/assembly] AssemblyPath  
```  
  
## 引数  
 out \=\/`FileName`  
 必須です。 .Pkgdef 出力ファイルの名前を設定```FileName`します。  
  
 \/codebase  
 省略可能です。 コードベース ユーティリティを使用して強制登録します。  
  
 \/assembly  
 アセンブリ ユーティリティを使用して登録を強制します。  
  
 `AssemblyPath`  
 .Pkgdef を生成する .dll ファイルのパス。  
  
## 解説  
 .Pkgdef ファイルを使用して拡張機能のデプロイには、Visual Studio の以前のバージョンのレジストリの要件が置き換えられます。  
  
 次の場所のいずれかで .pkgdef ファイルをインストールする必要があります: %localappdata%\\Microsoft\\Visual Studio\\14.0\\Extensions\\ または %vsinstalldir%\\common7\\ide\\extensions\\ します。 %Localappdata%\\Microsoft\\Visual Studio\\14.0\\Extensions\\ のインストール フォルダーには、拡張機能は、Visual Studio によって認識されますは既定で無効になります。 ユーザーを使用して、拡張機能を有効にできます **拡張機能と更新プログラム**します。 %Vsinstalldir%\\common7\\ide\\extensions\\ のインストール フォルダーには、既定で、拡張機能が有効にします。  
  
> [!NOTE]
>  **拡張機能と更新プログラム** VSIX パッケージの一部としてインストールされている場合を除き、拡張機能にアクセスするツールを使用することはできません。  
  
## 参照  
 [CreateExpInstance ユーティリティ](../../extensibility/internals/createexpinstance-utility.md)