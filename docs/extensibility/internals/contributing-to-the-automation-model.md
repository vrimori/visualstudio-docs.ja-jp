---
title: "オートメーション モデルに貢献している |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- automation [Visual Studio SDK]
ms.assetid: 44de482d-93c8-41a4-843c-cefda995a03e
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: bb69380913f188031c97b46530ea2659fc05fe30
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="contributing-to-the-automation-model"></a>オートメーション モデルに貢献しています。
Visual Studio は、環境をカスタマイズするためのオートメーション インターフェイスのセットを提供します。 オートメーション モデルは、エンドユーザーは Visual Studio のアドインおよび拡張機能を作成するオブジェクト モデルです。  
  
 さらは開発者として、VSPackage はオートメーション モデルに貢献する適切な場合、これにより、アドインを作成して、一般に、一貫性のあるユーザー エクスペリエンスを提供モデルで VSPackage を使用するときに VSPackage のエンドユーザーを有効に[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]です。  
  
 エンド ユーザー エクスペリエンスを一貫したさせるには、行うことができる一連のガイドライン、VSPackage のオートメーション モデルでアイデアに依存するように VSPackage を設計する際[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]です。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [オートメーション モデルの概要](../../extensibility/internals/automation-model-overview.md)  
 一般的な環境の主要なファセットを制御するオブジェクトの関連するグループとして、オートメーション モデルを定義します。 この一連のオブジェクトをオートメーション モデルの図に示しています。  
  
 [VSPackage でのオートメーションの提供](../../extensibility/internals/providing-automation-for-vspackages.md)  
 VSPackage のオートメーションを提供する 2 つの主な方法について説明します。  
  
 [プロジェクト オブジェクトの公開](../../extensibility/internals/exposing-project-objects.md)  
 VSPackage に固有のオブジェクトを作成するための手順を説明します。  
  
 [プロジェクトのモデリング](../../extensibility/internals/project-modeling.md)  
 新しいプロジェクトの種類のオートメーションを作成するために必要な標準的なプロジェクトのオブジェクトをについて説明し、プロジェクトの自動化に続くパスを示します。 このトピックでは、宣言とクラスの実装の番組表も提供します。  
  
 [イベントの公開](../../extensibility/internals/exposing-events-in-the-visual-studio-sdk.md)  
 イベント、オートメーション モデルを作成する詳細な手順についてを説明します。  
  
 [オプション ページのオートメーションのサポート](../../extensibility/internals/automation-support-for-options-pages.md)  
 カスタムの VSPackage のプロパティをサポートするために、オートメーション オブジェクトを返す方法について説明**オプション** ダイアログ ボックスで、**ツール**メニュー拡張することによって、`DTE.Properties`オブジェクト。  
  
 [コードのオートメーションの提供](../../extensibility/internals/providing-automation-for-code.md)  
 コードのオートメーション モデルを作成する必要がないことを説明します。 ただし、リンクはコード モデルにわかりやすい情報を提供するこのトピックで提供されます。  
  
 [方法: Windows 向けのオートメーションの提供](../../extensibility/internals/how-to-provide-automation-for-windows.md)  
 自動化を提供することがあることをお勧め、ウィンドウのオートメーション オブジェクトを使用できるようにして、環境が既製のオートメーション オブジェクトを既に提供していないときに説明します。 ツール ウィンドウおよびドキュメント ウィンドウのための自動化について説明します。  
  
 [オートメーション モデルの使用](../../extensibility/internals/using-the-automation-model.md)  
 オートメーション コンシューマーを取得する方法、初期プロジェクト オートメーション オブジェクトを示す 2 つのコード例を提供します。  
  
 [構成および SelectedItem オブジェクトのためのオートメーション](../../extensibility/internals/automation-for-configuration-and-selecteditem-objects.md)  
 構成オプションのための自動化と選択した項目の自動化についてを説明します。  
  
## <a name="reference"></a>参照  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>  
 DTE オートメーション オブジェクト モデルでは、VSPackage が参加する方法を示すコード サンプルを提供します。 パラメーター、戻り値、および選択した注釈の一覧を示します。  
  
## <a name="related-sections"></a>関連項目