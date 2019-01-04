---
title: プロジェクトの種類を作成する |Microsoft Docs
ms.date: 11/04/2016
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
ms.openlocfilehash: d80dd7fcaa75b5090145821307dfe7def28afbc1
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53987409"
---
# <a name="create-project-types"></a>プロジェクトの種類を作成します。
拡張する[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]を新しいプロジェクトの種類を作成します。 新しいプロジェクトの種類を作成するには、いくつかの概念を理解し、いくつかの手順を完了する必要があります。 次のトピックでは、プロジェクトの種類を作成する方法の概要を説明します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [プロジェクトの種類の設計に関する決定事項](../../extensibility/internals/project-type-design-decisions.md)  
 項目、プロジェクト ファイルの永続化、および新しいプロジェクトの種類を作成する前に作成する必要があるコミットメント メカニック設計上の決定について説明します。  
  
 [チェックリスト:新しいプロジェクトの種類を作成します。](../../extensibility/internals/checklist-creating-new-project-types.md)  
 コードの編集しコンパイル、ビルド、デバッグ、およびプロジェクト内のアプリケーションの配置などのプログラミング タスクをサポートする新しいプロジェクトの種類を作成する場合の手順の概要を示します。  
  
 [プロジェクト ファクトリを使用してプロジェクトのインスタンスを作成します。](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)  
 指定して新しいプロジェクトのインスタンスを作成するプロジェクト ファクトリを使用する方法について説明します。  
  
 [プロジェクトの種類を登録します。](../../extensibility/internals/registering-a-project-type.md)  
 ステートメントのレジストリから既定のパスとデータ、およびテーブルを提供するステートメントごとに、レジストリ スクリプトからのエントリが含まれているコード サンプルを提供します。  
  
 [プロジェクトの永続化](../../extensibility/internals/project-persistence.md)  
 使用について説明します`IPersistFileFormat`ファイルとファイル ベースのプロジェクトのオブジェクトの両方を保持します。  
  
 [MSBuild の使用](../../extensibility/internals/using-msbuild.md)  
 プロジェクトの種類を使用する方法について説明、[!INCLUDE[vstecmsbuild](../../extensibility/internals/includes/vstecmsbuild_md.md)]ビルドからビルドしてもらうためにエンジン[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]とコマンドライン。  
  
## <a name="related-sections"></a>関連項目  
 [シンボル参照ツールをサポートします。](../../extensibility/internals/supporting-symbol-browsing-tools.md)  
 などのツールを表示するコードのアーキテクチャについて説明します、**オブジェクト ブラウザー**と**クラス ビュー**ウィンドウ。 インターフェイスと、VSPackage でオブジェクトの参照を実装するために使用されるメソッドについて説明します。  
  
 [プロジェクトとプロジェクト項目テンプレートを追加します。](../../extensibility/internals/adding-project-and-project-item-templates.md)  
 プロジェクトがプロジェクト項目を開いたときにエディターが使用を決定するで再生する重要性について説明しますので、プロジェクト リソースを操作する方法。  
  
 [Windows インストーラーによる Vspackage をインストールします。](../../extensibility/internals/installing-vspackages-with-windows-installer.md)  
 Windows インストーラー パッケージに VSPackage Dll とその他の情報をラップする方法と、VSPackage に、独自の一意の id を付与する方法を示します (*します。MSI*ファイル) のお客様に展開します。  
  
 [Visual Studio での階層](../../extensibility/internals/hierarchies-in-visual-studio.md)  
 説明方法[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]ビューとアドレスの階層。  
  
 [VSPackage](../../extensibility/internals/vspackages.md)  
 インストール可能な COM オブジェクトを拡張する、VSPackage の概要を説明します、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]環境と、独自の VSPackage を実装する方法について説明します。  
  
 [プロジェクトの種類](../../extensibility/internals/project-types.md)  
 プロジェクトを使用してコードを変更、コンパイルしコード、ビルドし実行、コードをデバッグする方法について説明し、プロジェクトの種類を作成する方法についての詳細なトピックへのリンクを提供します。