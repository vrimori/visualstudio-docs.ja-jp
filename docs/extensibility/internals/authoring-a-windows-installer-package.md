---
title: Windows インストーラー パッケージの作成 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .msi files, VSPackages
- msi files, VSPackages
ms.assetid: 0ce7c21d-0d3f-47fe-a0bb-eed506e32609
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 93c69b2fba2bc866673b294a4f5c975a6ce3eb6a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55020947"
---
# <a name="author-a-windows-installer-package"></a>Windows インストーラー パッケージを作成します。
データ ドライブの Windows インストーラーのモデル。 にファイルをコピーし、レジストリ エントリを書き込む手続き型のスクリプトを作成するのではなくなどを作成するデータ ファイルおよびレジストリ データが含まれているデータベース テーブルの行と列。  
  
## <a name="database-entries"></a>データベース エントリ  
VSPackage をインストールするには、Windows インストーラー パッケージは、次のタスクを実行するデータベースのエントリを含める必要があります。  
  
- システムのバージョンを検索する検索[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)](AppSearch、CompLocator、RegLocator、DrLocator、および署名を含む Windows インストーラー テーブルを使用)、VSPackage がサポートしています。  
  
- サポートされているバージョンはない場合は、インストールをキャンセル[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]がインストールされている、VSPackage のもう 1 つのシステム要件が満たされていない場合 (起動条件のテーブルを使用) またはします。  
  
- VSPackage と (ディレクトリ、コンポーネント、およびファイル テーブルを使用) の依存ファイルをインストールします。  
  
- VSPackage の適切な情報を (レジストリのテーブルを使用して)、レジストリに追加します。  
  
- VSPackage の統合[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]呼び出して**devenv.exe/setup** (CustomAction テーブルを使用)。  
  
詳細については、次を参照してください。 [Windows インストーラー](/windows/desktop/Msi/windows-installer-portal)します。
  
## <a name="setup-tools"></a>セットアップ ツール  
さまざまなサードパーティ製のセットアップ ツールは、Windows インストーラー パッケージの開発環境を提供します。 次の無料ツールを使用できます。  
  
- InstallShield limited edition  
  
   Visual Studio で InstallShield の制限付きバージョンを取得できます**新しいプロジェクト**ダイアログ。 展開**その他のプロジェクトの種類**選び**セットアップと配置**します。 InstallShield のテンプレートを選択します。  
  
- Windows Installer XML ツールセット  
  
   Windows インストーラー XML (WiX) ツールセットは、XML ソース ファイルからの Windows インストーラー パッケージをビルドします。 WiX ツールセットは、Microsoft のオープン ソース プロジェクトです。 ソース コードおよび実行可能ファイルをダウンロードする[Wix ツールセット](http://sourceforge.net/projects/wix)します。  
  
   商用製品に統合する[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]を使用して、[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]を参照してください[ http://visualstudiogallery.com](http://visualstudiogallery.com/)します。  
  
## <a name="see-also"></a>関連項目  
 [Windows インストーラーによる Vspackage をインストールします。](../../extensibility/internals/installing-vspackages-with-windows-installer.md)