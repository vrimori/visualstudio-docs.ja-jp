---
title: "Windows インストーラー パッケージの作成 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Vspackage の .msi ファイル"
  - "Vspackage の msi ファイル"
ms.assetid: 0ce7c21d-0d3f-47fe-a0bb-eed506e32609
caps.latest.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 20
---
# Windows インストーラー パッケージの作成
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

データ ドライブの Windows インストーラーのモデル。 ファイルをコピーし、レジストリ エントリを記述する手順のスクリプトを作成する代わりになどを作成するファイルとレジストリ データを含むデータベース テーブルの行と列。  
  
## データベース エントリ  
 VSPackage をインストールするには、Windows インストーラー パッケージは、次のタスクを実行するデータベースのエントリを含める必要があります。  
  
-   バージョンを見つけるためのシステムを検索して [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 、VSPackage \(AppSearch、CompLocator、RegLocator、DrLocator、および署名を含む Windows インストーラー テーブルを使用\) をサポートしています。  
  
-   サポートされていないバージョンの場合は、インストールをキャンセル [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] がインストールされている VSPackage のもう 1 つのシステム要件が満たされていない場合 \(起動条件のテーブルを使用\) またはです。  
  
-   VSPackage と \(ディレクトリ、コンポーネント、およびファイル テーブルを使用\) の依存ファイルをインストールします。  
  
-   VSPackage の適切な情報をレジストリ \(レジストリ テーブルを使用\) に追加します。  
  
-   VSPackage での統合 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] を呼び出して **devenv.exe \/setup** \(CustomAction テーブルを使用\)。  
  
 詳細については、次を参照してください。 [Windows インストーラー](http://msdn.microsoft.com/library/cc185688\(VS.85\).aspx)します。  
  
## ツールをセットアップします。  
 さまざまなサードパーティ製のセットアップのツールは、Windows インストーラー パッケージの開発環境を提供します。 2 つの無償ツール、次のとおりです。  
  
-   InstallShield Limited Edition  
  
     Visual Studio で InstallShield の制限されたバージョンを取得できます **新しいプロジェクト** ダイアログ。 展開 **その他のプロジェクトの種類** し、\[ **セットアップと配置**します。 InstallShield のテンプレートを選択します。  
  
-   Windows Installer XML Toolset  
  
     ツールセットは、XML ソース ファイルからの Windows インストーラー パッケージをビルドします。 ツールセットは、Microsoft のオープン ソース プロジェクトです。 ソース コードと実行可能ファイルをダウンロードする [http:\/\/sourceforge.net\/projects\/wix](http://sourceforge.net/projects/wix)します。  
  
 統合できる商用製品の [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] を使用して、 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], を参照してください [http:\/\/visualstudiogallery.com](http://visualstudiogallery.com/)します。  
  
## 参照  
 [Windows インストーラーである Vspackage をインストールします。](../../extensibility/internals/installing-vspackages-with-windows-installer.md)