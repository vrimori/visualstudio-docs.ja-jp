---
title: "Windows インストーラーである Vspackage をインストールします。 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Windows インストーラーを使用してインストール [Visual Studio SDK]"
  - "Vspackage を展開します。"
ms.assetid: 41d2c72c-0a97-4fcd-b3aa-33a8d3aa962a
caps.latest.revision: 30
caps.handback.revision: 30
ms.author: "gregvanl"
manager: "ghogen"
---
# Windows インストーラーである Vspackage をインストールします。
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] に VSPackage を統合するとユーザーのコンピューターにファイルをコピーが必要です。  VSPackage のインストーラーにはVSPackage とその依存ファイルとインストール登録 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] に統合する必要があります。  VSPackage は [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] のスプラッシュ スクリーンとダイアログ ボックスのアイコンの表示など統合機能を利用できます。  
  
 Microsoft Windows インストーラー ファイルはVSPackages を配布することをお勧めします。  簡単に Windows インストーラー パッケージは [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] でサポートされているすべての Windows オペレーティング システムで実行できます。  詳細については、「[Windows Installer](http://msdn.microsoft.com/ja-jp/121be21b-b916-43e2-8f10-8b080516d2a0)」を参照してください。  
  
## このセクションの内容  
 [Windows インストーラーの基本概念](../../extensibility/internals/windows-installer-basics.md)  
 Windows インストーラーの概要について説明します。  
  
 [VSPackage のセットアップのシナリオ](../../extensibility/internals/vspackage-setup-scenarios.md)  
 VSPackage と[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 両方のインストールをサポートするさまざまな方法について説明します。  
  
 [Windows インストーラー パッケージの作成](../../extensibility/internals/authoring-a-windows-installer-package.md)  
 インストーラーを [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] に正しくインストールしに統合する VSPackage を次の一般的な手順の概要を説明します。  
  
 [システム要件の検出](../../extensibility/internals/detecting-system-requirements.md)  
 VSPackage の要件を満たすインストーラーが [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] とコンポーネントおよびキャンセルの設定を検出する方法について説明します。  
  
 [コンポーネントの管理](../../extensibility/internals/component-management.md)  
 以前のバージョンの製品の整合性を保持するインストーラーを開発する方法について説明します。  
  
 [VSPackage のインストール ディレクトリを選択します。](../../extensibility/internals/choosing-the-installation-directory-for-a-vspackage.md)  
 VSPackage を検索するためのオプションを示します。  
  
 [VSPackage の登録](../../extensibility/internals/vspackage-registration.md)  
 VSPackage をインストール時に登録されている今度自己登録が不正な概念であるかについて説明します。  
  
 [プロジェクトの種類を展開します。](../../extensibility/internals/deploying-project-types.md)  
 マネージ コード プロジェクトの種類に対して新しいプロジェクトの種類のアグリゲーターを使用する方法について説明します。  
  
 [方法: インストーラーのレジストリ情報を生成します。](../../extensibility/internals/how-to-generate-registry-information-for-an-installer.md)  
 RegPkg.exe をマネージ VSPackage のレジスタ マニフェストを生成する方法について説明します。  
  
 [インストール後に実行する必要がありますコマンド](../../extensibility/internals/commands-that-must-be-run-after-installation.md)  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] に VSPackage を統合するインストール後のコマンドを実装する方法について説明します。  
  
 [Windows インストーラーで VSPackage をアンインストールします。](../../extensibility/internals/uninstalling-a-vspackage-with-windows-installer.md)  
 ユーザーが VSPackage をインストールするとインストーラーが手順について説明します。  
  
## 関連項目  
 [VSPackage のインストール](../../misc/installing-vspackages.md)  
 VSPackage をビルド [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] のインストール方法と同時に複数のバージョンであるユーザーをサポートする方法について説明します。