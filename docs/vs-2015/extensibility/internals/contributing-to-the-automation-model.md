---
title: オートメーション モデルに貢献する |Microsoft Docs
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
- automation [Visual Studio SDK]
ms.assetid: 44de482d-93c8-41a4-843c-cefda995a03e
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 53a669ed6f1ddaa9c2274371439828da24b92789
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51726974"
---
# <a name="contributing-to-the-automation-model"></a>オートメーション モデルへの投稿
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Visual Studio は、環境をカスタマイズするためのオートメーション インターフェイスのセットを提供します。 オートメーション モデルは、エンドユーザーは Visual Studio のアドインと拡張機能を作成するオブジェクト モデルです。  
  
 さらは、VSPackage 開発者は、オートメーション モデルに貢献する適切ですこれにより、アドインを作成し、一般に一貫性のあるユーザー エクスペリエンスを提供モデルで、VSPackage を使用するときに、VSPackage のエンドユーザーを有効に[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]します。  
  
 エンドユーザーのエクスペリエンスを一貫したさせるには、利用できる一連のガイドライン、VSPackage のオートメーション モデルでアイデアに依存するために VSPackage をデザインする[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [オートメーション モデルの概要](../../extensibility/internals/automation-model-overview.md)  
 一般的な環境の主要な側面を制御するオブジェクトの関連するグループとして、オートメーション モデルを定義します。 この一連のオブジェクトは、オートメーション モデルのダイアグラムに示されています。  
  
 [VSPackage でのオートメーションの提供](../../extensibility/internals/providing-automation-for-vspackages.md)  
 VSPackage のオートメーションを提供する 2 つの主な方法について説明します。  
  
 [プロジェクト オブジェクトの公開](../../extensibility/internals/exposing-project-objects.md)  
 VSPackage に固有のオブジェクトを作成するための手順について説明します。  
  
 [プロジェクトのモデリング](../../extensibility/internals/project-modeling.md)  
 新しいプロジェクトの種類の自動化を作成するために必要な標準的なプロジェクト オブジェクトを説明し、プロジェクトの自動化に続くパスを示しています。 このトピックでは、宣言と実装クラスの一覧も提供します。  
  
 [イベントの公開](../../extensibility/internals/exposing-events-in-the-visual-studio-sdk.md)  
 オートメーション モデルのイベントを作成するための手順について説明します。  
  
 [オプション ページのオートメーションのサポート](../../extensibility/internals/automation-support-for-options-pages.md)  
 VSPackage のプロパティをサポートしているカスタムのオートメーション オブジェクトを取得する方法について説明します**オプション** ダイアログ ボックスで、**ツール**メニューを拡張することによって、`DTE.Properties`オブジェクト。  
  
 [コードのオートメーションの提供](../../extensibility/internals/providing-automation-for-code.md)  
 コードのオートメーション モデルを作成する必要がないことについて説明します。 ただし、このトピックの「コード モデルに洞察力に富んだ情報を提供するリンクが提供されます。  
  
 [方法: Windows 向けのオートメーションの提供](../../extensibility/internals/how-to-provide-automation-for-windows.md)  
 オートメーションを提供することことをお勧め、ウィンドウでオートメーション オブジェクトを使用できるようにして、環境に既に既製のオートメーション オブジェクトを提供しないときに説明します。 ツール ウィンドウおよびドキュメント ウィンドウのための自動化について説明します。  
  
 [オートメーション モデルの使用](../../extensibility/internals/using-the-automation-model.md)  
 Automation の消費者を取得する方法、初期のプロジェクト オートメーション オブジェクトを示す 2 つのコード例を提供します。  
  
 [構成および SelectedItem オブジェクトのためのオートメーション](../../extensibility/internals/automation-for-configuration-and-selecteditem-objects.md)  
 構成オプションのための自動化と選択した項目の自動化についてを説明します。  
  
## <a name="reference"></a>参照  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>  
 VSPackage が、DTE オートメーション オブジェクト モデルに参加する方法を示すコード サンプルを提供します。 パラメーター、戻り値、および選択した注釈の一覧を表示します。  
  
## <a name="related-sections"></a>関連項目

