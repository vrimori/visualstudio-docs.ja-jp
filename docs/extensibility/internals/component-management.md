---
title: "コンポーネントの管理 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "コンポーネントのインストール [Visual Studio SDK]"
  - "インストール [Visual Studio SDK] ファイルの管理"
ms.assetid: 029bffa2-6841-4caa-a41a-442467e1aedc
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# コンポーネントの管理
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Windows インストーラーのタスクの単位は Windows インストーラーのコンポーネントと呼ばれます \(WICs またはそのコンポーネントと呼ばれます\)。  GUID は Windows インストーラーを使用してインストールと設定のために参照カウントの基本単位であり各 WIC を示します。  
  
 VSPackage のインストーラーを作成するには複数の製品を使用できますがこの説明はWindows インストーラー \(.msi\) ファイルの使用を前提としています。  インストーラーを作成した場合は正しい参照カウントが発生するたびにファイルの配置を管理する必要があります。  その結果製品のバージョンはに干渉せずインストールのミックスで互いを中断しシナリオをアンマネージ インストールされません。  
  
 Windows インストーラーでは参照カウントがコンポーネント レベルに発生します。  —コンポーネントを慎重に\[リソース \(ファイルレジストリ エントリなど整理しておく必要があります。  組織の他のレベルがあります。モジュール異なるシナリオに役立つ機能と製品のような。  詳細については、「[Windows インストーラーの基本概念](../../extensibility/internals/windows-installer-basics.md)」を参照してください。  
  
## インストールの設定を作成する場合のガイドライン  
  
-   独自のコンポーネントのバージョン間で共有するレジストリ キーとファイルを作成します。  
  
     これは簡単に次のバージョンで実行できるようになります。  たとえばグローバルに登録された typelibファイル名の拡張子は HKEY\_CLASSES\_ROOT で他の項目など登録します。  
  
-   別のマージ モジュールに共有コンポーネントをグループ化します。  
  
     これはside\-by\-side 前方に移動用に正しく作成に役立ちます。  
  
-   バージョン間で同じ Windows インストーラー コンポーネントを使用して共有ファイルとレジストリ キーをインストールします。  
  
     コンポーネントを使用するとVSPackage 付きバージョン 1 がインストールされますがVSPackage別のがまだインストール時にファイルレジストリ エントリアンマネージ インストールされます。  
  
-   同じコンポーネントのバージョン管理と共有項目を混在させないようにします。  
  
     そのためにはグローバル共有場所に分離された位置に項目とバージョン付きの項目をインストールすることはできなくなります。  
  
-   バージョン管理されたファイルを指すレジストリ キーが共有されていません。  
  
     共有キーは別のバージョン付き VSPackage をインストールするとき上書きされます。  ファイルを削除したらキー ポイントする 2 番目のバージョンは移動します。  
  
## 参照  
 [共有およびバージョン管理の VSPackages の使い分け](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)   
 [VSPackage のセットアップのシナリオ](../../extensibility/internals/vspackage-setup-scenarios.md)