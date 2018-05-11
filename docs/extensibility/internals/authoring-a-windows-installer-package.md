---
title: Windows インストーラー パッケージの作成 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- .msi files, VSPackages
- msi files, VSPackages
ms.assetid: 0ce7c21d-0d3f-47fe-a0bb-eed506e32609
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 215e1496d35059448cf11457658b7d1270b5677d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="authoring-a-windows-installer-package"></a>Windows インストーラー パッケージの作成
データ ドライブの Windows インストーラーのモデル。 ファイルをコピーし、レジストリ エントリを記述する手順のスクリプトを記述するのではなくなどを作成するファイルとレジストリ データを含むデータベース テーブルの行と列。  
  
## <a name="database-entries"></a>[データベース エントリ]  
 VSPackage をインストールするには、Windows インストーラー パッケージは、次のタスクを実行するデータベースのエントリを含める必要があります。  
  
-   バージョンを見つけるためのシステムを検索して[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]VSPackage が (AppSearch、CompLocator、RegLocator、DrLocator、および署名を含む Windows インストーラー テーブルの使用) をサポートします。  
  
-   サポートされていないバージョンの場合は、インストールをキャンセル[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]がインストールされている、VSPackage の他のシステムの要件が満たされていない場合 (起動条件のテーブルを使用) またはします。  
  
-   VSPackage と (ディレクトリ、コンポーネント、およびファイル テーブルを使用) の依存ファイルをインストールします。  
  
-   VSPackage の適切な情報を (レジストリの表に、使用して)、レジストリに追加します。  
  
-   VSPackage の統合[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]を呼び出して**devenv.exe/setup** (CustomAction テーブルを使用)。  
  
 詳細については、次を参照してください。 [Windows インストーラー](http://msdn.microsoft.com/library/cc185688\(VS.85\).aspx)です。  
  
## <a name="setup-tools"></a>セットアップ ツール  
 さまざまなサード パーティ製のセットアップ ツールは、Windows インストーラー パッケージの開発環境を提供します。 2 つの無料ツール次に示します。  
  
-   InstallShield Limited Edition  
  
     Visual Studio で InstallShield の制限付きのバージョンを取得できます**新しいプロジェクト**ダイアログ。 展開**その他のプロジェクトの種類**し、**セットアップと配置**です。 InstallShield のテンプレートを選択します。  
  
-   Windows Installer XML Toolset  
  
     ツールセットは、XML ソース ファイルから Windows インストーラー パッケージを構築します。 ツールセットは、Microsoft のオープン ソース プロジェクトです。 ソース コードとから実行可能ファイルをダウンロードすることができます[ http://sourceforge.net/projects/wix](http://sourceforge.net/projects/wix)です。  
  
 統合できる商用の製品の[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]を使用して、[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]を参照してください[ http://visualstudiogallery.com](http://visualstudiogallery.com/)です。  
  
## <a name="see-also"></a>関連項目  
 [Windows インストーラーによる VSPackage のインストール](../../extensibility/internals/installing-vspackages-with-windows-installer.md)