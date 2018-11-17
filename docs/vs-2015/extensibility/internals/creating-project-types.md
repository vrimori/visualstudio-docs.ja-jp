---
title: プロジェクトの種類を作成する |Microsoft Docs
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
- project types, new
- projects [Visual Studio SDK], new project types
ms.assetid: bdb2d22e-d622-450c-bb2d-98152a745fcf
caps.latest.revision: 26
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 58b31e363d78af7902e6174c9683b7e794031263
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51756205"
---
# <a name="creating-project-types"></a>プロジェクト タイプの作成
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

拡張する[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]を新しいプロジェクトの種類を作成します。 新しいプロジェクトの種類を作成するには、いくつかの概念を理解し、いくつかの手順を完了する必要があります。 次のトピックでは、プロジェクトの種類を作成する方法の概要を説明します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [プロジェクト タイプのデザインの方針](../../extensibility/internals/project-type-design-decisions.md)  
 項目、プロジェクト ファイルの永続化、および新しいプロジェクトの種類を作成する前に作成する必要があるコミットメント メカニック設計上の決定について説明します。  
  
 [チェック リスト: 新しいプロジェクト タイプの作成](../../extensibility/internals/checklist-creating-new-project-types.md)  
 コードの編集しコンパイル、ビルド、デバッグ、およびプロジェクト内のアプリケーションの配置のプログラミング タスクをサポートする新しいプロジェクトの種類を作成する場合の手順の概要を示します。  
  
 [プロジェクト ファクトリを使用したプロジェクト インスタンスの作成](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)  
 指定して新しいプロジェクトのインスタンスを作成するプロジェクト ファクトリを使用する方法について説明します。  
  
 [プロジェクト タイプの登録](../../extensibility/internals/registering-a-project-type.md)  
 ステートメントのレジストリから既定のパスとデータ、およびテーブルを提供するステートメントごとに、レジストリ スクリプトからのエントリが含まれているコード サンプルを提供します。  
  
 [プロジェクトの永続化](../../extensibility/internals/project-persistence.md)  
 使用について説明します`IPersistFileFormat`ファイルとファイル ベースのプロジェクトのオブジェクトの両方を保持します。  
  
 [MSBuild の使用](../../extensibility/internals/using-msbuild.md)  
 プロジェクトの種類を使用する方法について説明、[!INCLUDE[vstecmsbuild](../../includes/vstecmsbuild-md.md)]ビルドからビルドしてもらうためにエンジン[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]とコマンドライン。  
  
## <a name="related-sections"></a>関連項目  
 [シンボル参照ツールのサポート](../../extensibility/internals/supporting-symbol-browsing-tools.md)  
 などのツールを表示するコードのアーキテクチャについて説明します、**オブジェクト ブラウザー**と**クラス ビュー**ウィンドウ。 インターフェイスと、VSPackage でオブジェクトの参照を実装するために使用されるメソッドについて説明します。  
  
 [プロジェクト テンプレートとプロジェクト項目テンプレートの追加](../../extensibility/internals/adding-project-and-project-item-templates.md)  
 プロジェクトがプロジェクト項目を開いたときにエディターが使用を決定するで再生する重要性について説明しますので、プロジェクト リソースを操作する方法。  
  
 [Windows インストーラーによる VSPackage のインストール](../../extensibility/internals/installing-vspackages-with-windows-installer.md)  
 Windows インストーラー パッケージに VSPackage Dll とその他の情報をラップする方法と、VSPackage に、独自の一意の id を付与する方法を示します (します。MSI ファイル) のお客様に展開します。  
  
 [Visual Studio での階層](../../extensibility/internals/hierarchies-in-visual-studio.md)  
 説明方法[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]ビューとアドレスの階層。  
  
 [VSPackage](../../extensibility/internals/vspackages.md)  
 インストール可能な COM オブジェクトを拡張する、VSPackage の概要を説明します、[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]環境と、独自の VSPackage を実装する方法について説明します。  
  
 [プロジェクト タイプ](../../extensibility/internals/project-types.md)  
 プロジェクトを使用してコードを変更、コンパイルしコード、ビルドし実行、コードをデバッグする方法について説明し、プロジェクトの種類を作成する方法についての詳細なトピックへのリンクを提供します。

