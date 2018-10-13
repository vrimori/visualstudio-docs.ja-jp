---
title: Windows インストーラーによる Vspackage のインストール |Microsoft Docs
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
- installation [Visual Studio SDK], with Windows Installer
- VSPackages, deploying
ms.assetid: 41d2c72c-0a97-4fcd-b3aa-33a8d3aa962a
caps.latest.revision: 31
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ae0e99b278924a123410f5590cea9f8239acd9ad
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49227969"
---
# <a name="installing-vspackages-with-windows-installer"></a>Windows インストーラーによる VSPackage のインストール
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

VSPackage の統合[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]だけで複数のユーザーのコンピューターにファイルをコピーする必要があります。 VSPackage とその依存ファイルをインストールして登録し、それらを統合する必要があります VSPackage のインストーラー[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]します。 VSPackage がのアイコンを表示するなどの統合機能の活用、[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]スプラッシュ画面とダイアログ ボックスの詳細。  
  
 Microsoft Windows インストーラー ファイルは、Vspackage を配布することをお勧めの方法です。 サポートされている任意の Windows オペレーティング システムで使いやすい Windows インストーラー パッケージを実行できる[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]します。 詳細については、次を参照してください。 [Windows インストーラー](http://msdn.microsoft.com/en-us/121be21b-b916-43e2-8f10-8b080516d2a0)します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [Windows インストーラーの基本事項](../../extensibility/internals/windows-installer-basics.md)  
 Windows インストーラーの概要を示します。  
  
 [VSPackage のセットアップ シナリオ](../../extensibility/internals/vspackage-setup-scenarios.md)  
 両方の Vspackage のサイド バイ サイドでインストールをサポートするさまざまな方法について説明しますと[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]します。  
  
 [Windows インストーラー パッケージの編集](../../extensibility/internals/authoring-a-windows-installer-package.md)  
 インストーラーが正しくインストールしに Vspackage を統合する次の一般的な手順の概要を示します[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]します。  
  
 [システム要件の検出](../../extensibility/internals/detecting-system-requirements.md)  
 インストーラーが検出できる方法について説明します。[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]および VSPackage の要件が満たされない場合にセットアップのコンポーネントとキャンセルします。  
  
 [コンポーネント管理](../../extensibility/internals/component-management.md)  
 以前の製品バージョンの整合性を保持するインストーラーを開発する方法について説明します。  
  
 [VSPackage のインストール ディレクトリの選択](../../extensibility/internals/choosing-the-installation-directory-for-a-vspackage.md)  
 Vspackage を検索するためのオプションをまとめたものです。  
  
 [VSPackage の登録](../../extensibility/internals/vspackage-registration.md)  
 インストール時に Vspackage を登録する方法について説明し、理由、登録はお勧めします。  
  
 [プロジェクト タイプの配置](../../extensibility/internals/deploying-project-types.md)  
 マネージ コード プロジェクトの種類の新しいプロジェクトの種類のアグリゲーターを使用する方法について説明します。  
  
 [方法: インストーラー向けの登録情報の生成](../../extensibility/internals/how-to-generate-registry-information-for-an-installer.md)  
 RegPkg.exe を使用して、マネージ VSPackage を登録するマニフェストを生成する方法について説明します。  
  
 [インストール後に実行する必要があるコマンド](../../extensibility/internals/commands-that-must-be-run-after-installation.md)  
 Vspackage を統合するインストール後のコマンドを実行する方法について説明します[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]します。  
  
 [Windows インストーラーによる VSPackage のアンインストール](../../extensibility/internals/uninstalling-a-vspackage-with-windows-installer.md)  
 ユーザー、VSPackage をアンインストールすると、インストーラーを実行する必要がありますの手順について説明します。  
  
## <a name="related-sections"></a>関連項目  
 [VSPackage のインストール](../../misc/installing-vspackages.md)  
 ビルドして、Vspackage をインストールする方法と複数のバージョンを実行しているユーザーをサポートする方法について説明しますの[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]と同時にします。

