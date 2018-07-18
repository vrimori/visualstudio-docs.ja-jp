---
title: プロジェクトの種類を作成 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project types, new
- projects [Visual Studio SDK], new project types
ms.assetid: bdb2d22e-d622-450c-bb2d-98152a745fcf
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: aa58b0195c0fbcf50cce0ac5300ab142c4de93d0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31129959"
---
# <a name="creating-project-types"></a>プロジェクトの種類を作成します。
拡張できます[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]を新しいプロジェクトの種類を作成します。 新しいプロジェクトの種類を作成するには、いくつかの概念を理解し、いくつかの手順を完了する必要があります。 次のトピックでは、プロジェクトの種類を作成する方法の概要を説明します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [プロジェクト タイプのデザインの方針](../../extensibility/internals/project-type-design-decisions.md)  
 項目、プロジェクト ファイルの永続性、および新しいプロジェクトの種類を作成する前に確認する必要があるコミットメント メカニック デザインの決定について説明します。  
  
 [チェック リスト: 新しいプロジェクト タイプの作成](../../extensibility/internals/checklist-creating-new-project-types.md)  
 コードの編集およびコンパイルする、ビルド、デバッグ、およびプロジェクトでアプリケーションの配置のプログラミング タスクをサポートする新しいプロジェクトの種類を作成する手順の概要を示します。  
  
 [プロジェクト ファクトリを使用したプロジェクト インスタンスの作成](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)  
 提供し、プロジェクト ファクトリを使用して、新しいプロジェクトのインスタンスを作成する方法について説明します。  
  
 [プロジェクト タイプの登録](../../extensibility/internals/registering-a-project-type.md)  
 ステートメントのレジストリから既定のパスとデータ、およびテーブルを提供するステートメントごとに、レジストリ スクリプトのエントリが含まれたコード サンプルを提供します。  
  
 [プロジェクトの永続化](../../extensibility/internals/project-persistence.md)  
 使用について説明`IPersistFileFormat`ファイルとプロジェクトのファイル ベースのオブジェクトの両方を維持します。  
  
 [MSBuild の使用](../../extensibility/internals/using-msbuild.md)  
 プロジェクトの種類の使用方法について説明します、[!INCLUDE[vstecmsbuild](../../extensibility/internals/includes/vstecmsbuild_md.md)]ビルドからビルドできるようにするエンジン[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]およびコマンドラインでします。  
  
## <a name="related-sections"></a>関連項目  
 [シンボル参照ツールのサポート](../../extensibility/internals/supporting-symbol-browsing-tools.md)  
 などのツールを表示するコードのアーキテクチャについて説明します、**オブジェクト ブラウザー**と**クラス ビュー**ウィンドウです。 インターフェイスとオブジェクト参照を VSPackage に実装するために使用する方法について説明します。  
  
 [プロジェクト テンプレートとプロジェクト項目テンプレートの追加](../../extensibility/internals/adding-project-and-project-item-templates.md)  
 プロジェクトを再生するエディターを使用してプロジェクト項目を開いたときに決定する重要性について説明しますので、プロジェクト リソースを操作する方法です。  
  
 [Windows インストーラーによる VSPackage のインストール](../../extensibility/internals/installing-vspackages-with-windows-installer.md)  
 VSPackage、独自の一意の id を付与する方法と、Windows インストーラー パッケージに、VSPackage の Dll やその他の情報をラップする方法を示しています (です。MSI ファイル) の顧客に展開します。  
  
 [Visual Studio での階層](../../extensibility/internals/hierarchies-in-visual-studio.md)  
 説明方法[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]ビューとアドレスの階層です。  
  
 [VSPackage](../../extensibility/internals/vspackages.md)  
 VSPackage、インストール可能な COM オブジェクトを拡張するの概要を示します、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]環境と、独自の VSPackage を実装する方法について説明します。  
  
 [プロジェクト タイプ](../../extensibility/internals/project-types.md)  
 プロジェクトを使用してコードを変更、コンパイルしコード、ビルドおよび実行し、コードをデバッグする方法について説明し、プロジェクトの種類を作成する方法の詳細なトピックへのリンクを提供します。