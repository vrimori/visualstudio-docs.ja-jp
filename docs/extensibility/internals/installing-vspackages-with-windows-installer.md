---
title: Windows インストーラーで Vspackage をインストールする |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- installation [Visual Studio SDK], with Windows Installer
- VSPackages, deploying
ms.assetid: 41d2c72c-0a97-4fcd-b3aa-33a8d3aa962a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6fafebe0dc2bb8e13c99be8b340e7f5663a9930f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31131007"
---
# <a name="installing-vspackages-with-windows-installer"></a>Windows インストーラーで Vspackage をインストールします。
VSPackage を統合する[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]単ユーザーのコンピューターにファイルのコピーが必要です。 VSPackage とその依存ファイルをインストールし、登録およびにそれらを統合する必要があります、VSPackage のインストーラー[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]です。 VSPackage がのアイコンを表示するなどの統合機能の活用、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]スプラッシュ スクリーンとについて ダイアログ ボックス。  
  
 Microsoft Windows インストーラ ファイルは、Vspackage を配布することをお勧めします。 使いやすい Windows インストーラー パッケージでサポートされている任意の Windows オペレーティング システム上で実行できる[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]です。 詳細については、次を参照してください。 [Windows インストーラー](http://msdn.microsoft.com/en-us/121be21b-b916-43e2-8f10-8b080516d2a0)です。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [Windows インストーラーの基本事項](../../extensibility/internals/windows-installer-basics.md)  
 Windows インストーラーの概要を示します。  
  
 [VSPackage のセットアップ シナリオ](../../extensibility/internals/vspackage-setup-scenarios.md)  
 両方の Vspackage のサイド バイ サイド インストールをサポートするさまざまな方法について説明し、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]です。  
  
 [Windows インストーラー パッケージの編集](../../extensibility/internals/authoring-a-windows-installer-package.md)  
 インストーラーが正しくインストールしに Vspackage を統合する次の一般的な手順の概要を説明[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]です。  
  
 [システム要件の検出](../../extensibility/internals/detecting-system-requirements.md)  
 インストーラーが検出できる方法について説明します[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]とそのコンポーネントと [キャンセル] セットアップは VSPackage の要件が満たされない場合。  
  
 [コンポーネント管理](../../extensibility/internals/component-management.md)  
 以前の製品バージョンの整合性を維持するインストーラーを開発する方法について説明します。  
  
 [VSPackage のインストール ディレクトリの選択](../../extensibility/internals/choosing-the-installation-directory-for-a-vspackage.md)  
 Vspackage を検索するためのオプションをまとめたものです。  
  
 [VSPackage の登録](../../extensibility/internals/vspackage-registration.md)  
 インストール時に Vspackage を登録する方法について説明し、理由自己登録をお勧めが正しくありません。  
  
 [プロジェクト タイプの配置](../../extensibility/internals/deploying-project-types.md)  
 マネージ コード プロジェクトの種類の新しいプロジェクトの種類アグリゲーターを使用する方法について説明します。  
  
 [方法: インストーラー向けの登録情報の生成](../../extensibility/internals/how-to-generate-registry-information-for-an-installer.md)  
 RegPkg.exe を使用して、マネージ VSPackage の登録のマニフェストを生成する方法について説明します。  
  
 [インストール後に実行する必要があるコマンド](../../extensibility/internals/commands-that-must-be-run-after-installation.md)  
 Vspackage を統合するインストール後のコマンドを実行する方法について説明します[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]です。  
  
 [Windows インストーラーによる VSPackage のアンインストール](../../extensibility/internals/uninstalling-a-vspackage-with-windows-installer.md)  
 ユーザー、VSPackage をアンインストールするときに、インストーラーを実行する必要がありますの手順について説明します。  