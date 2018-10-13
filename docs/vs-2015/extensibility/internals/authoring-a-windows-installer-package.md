---
title: Windows インストーラー パッケージの作成 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- .msi files, VSPackages
- msi files, VSPackages
ms.assetid: 0ce7c21d-0d3f-47fe-a0bb-eed506e32609
caps.latest.revision: 21
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2ed245a1d26be951f6cada4b8ae58c158102d190
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49198278"
---
# <a name="authoring-a-windows-installer-package"></a>Windows インストーラー パッケージの編集
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

データ ドライブの Windows インストーラーのモデル。 にファイルをコピーし、レジストリ エントリを書き込む手続き型のスクリプトを作成するのではなくなどを作成するデータ ファイルおよびレジストリ データが含まれているデータベース テーブルの行と列。  
  
## <a name="database-entries"></a>[データベース エントリ]  
 VSPackage をインストールするには、Windows インストーラー パッケージは、次のタスクを実行するデータベースのエントリを含める必要があります。  
  
-   システムのバージョンを検索する検索[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)](AppSearch、CompLocator、RegLocator、DrLocator、および署名を含む Windows インストーラー テーブルを使用)、VSPackage がサポートしています。  
  
-   サポートされているバージョンはない場合は、インストールをキャンセル[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]がインストールされている、VSPackage のもう 1 つのシステム要件が満たされていない場合 (起動条件のテーブルを使用) またはします。  
  
-   VSPackage と (ディレクトリ、コンポーネント、およびファイル テーブルを使用) の依存ファイルをインストールします。  
  
-   VSPackage の適切な情報を (レジストリのテーブルを使用して)、レジストリに追加します。  
  
-   VSPackage の統合[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]呼び出して**devenv.exe/setup** (CustomAction テーブルを使用)。  
  
 詳細については、次を参照してください。 [Windows インストーラー](http://msdn.microsoft.com/library/cc185688\(VS.85\).aspx)します。  
  
## <a name="setup-tools"></a>セットアップ ツール  
 さまざまなサードパーティ製のセットアップ ツールは、Windows インストーラー パッケージの開発環境を提供します。 2 つの無償ツール、次に示します。  
  
-   InstallShield Limited Edition  
  
     Visual Studio で InstallShield の制限付きバージョンを取得できます**新しいプロジェクト**ダイアログ。 展開**その他のプロジェクトの種類**選び**セットアップと配置**します。 InstallShield のテンプレートを選択します。  
  
-   Windows Installer XML Toolset  
  
     ツールセットは、XML ソース ファイルからの Windows インストーラー パッケージをビルドします。 ツールセットは、Microsoft オープン ソース プロジェクトです。 ソース コードおよび実行可能ファイルをダウンロードする[ http://sourceforge.net/projects/wix](http://sourceforge.net/projects/wix)します。  
  
 商用製品に統合する[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]を使用して、[!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)]を参照してください[ http://visualstudiogallery.com](http://visualstudiogallery.com/)します。  
  
## <a name="see-also"></a>関連項目  
 [Windows インストーラーによる VSPackage のインストール](../../extensibility/internals/installing-vspackages-with-windows-installer.md)

