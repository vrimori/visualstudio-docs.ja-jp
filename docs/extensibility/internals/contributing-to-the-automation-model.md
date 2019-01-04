---
title: オートメーション モデルに貢献する |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK]
ms.assetid: 44de482d-93c8-41a4-843c-cefda995a03e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6db9cd21b56fb4d31a97fea9f16541377a8de1f3
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53952603"
---
# <a name="contribute-to-the-automation-model"></a>オートメーション モデルに貢献します。
Visual Studio は、環境をカスタマイズするためのオートメーション インターフェイスのセットを提供します。 オートメーション モデルは、エンドユーザーは Visual Studio のアドインと拡張機能を作成するオブジェクト モデルです。  
  
 さらは、VSPackage 開発者は、オートメーション モデルに貢献する適切ですこれにより、アドインを作成し、一般に一貫性のあるユーザー エクスペリエンスを提供モデルで、VSPackage を使用するときに、VSPackage のエンドユーザーを有効に[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]します。  
  
 エンドユーザーのエクスペリエンスを一貫したさせるには、利用できる一連のガイドライン、VSPackage のオートメーション モデルでアイデアに依存するために VSPackage をデザインする[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [オートメーション モデルの概要](../../extensibility/internals/automation-model-overview.md)  
 一般的な環境の主要な側面を制御するオブジェクトの関連するグループとして、オートメーション モデルを定義します。 この一連のオブジェクトは、オートメーション モデルのダイアグラムに示されています。  
  
 [Vspackage のオートメーションを提供します。](../../extensibility/internals/providing-automation-for-vspackages.md)  
 VSPackage のオートメーションを提供する 2 つの主な方法について説明します。  
  
 [プロジェクト オブジェクトを公開します。](../../extensibility/internals/exposing-project-objects.md)  
 VSPackage に固有のオブジェクトを作成するための手順について説明します。  
  
 [プロジェクトのモデリング](../../extensibility/internals/project-modeling.md)  
 新しいプロジェクトの種類の自動化を作成するために必要な標準的なプロジェクト オブジェクトを説明し、プロジェクトの自動化に続くパスを示しています。 このトピックでは、宣言と実装クラスの一覧も提供します。  
  
 [イベントを公開します。](../../extensibility/internals/exposing-events-in-the-visual-studio-sdk.md)  
 オートメーション モデルのイベントを作成するための手順について説明します。  
  
 [[オプション] ページのオートメーションをサポートします。](../../extensibility/internals/automation-support-for-options-pages.md)  
 VSPackage のプロパティをサポートしているカスタムのオートメーション オブジェクトを取得する方法について説明します**オプション** ダイアログ ボックスで、**ツール**メニューを拡張することによって、`DTE.Properties`オブジェクト。  
  
 [コードのオートメーションを提供します。](../../extensibility/internals/providing-automation-for-code.md)  
 コードのオートメーション モデルを作成する必要がないことについて説明します。 ただし、このトピックの「コード モデルに洞察力に富んだ情報を提供するリンクが提供されます。  
  
 [方法: Windows のオートメーションを提供します。](../../extensibility/internals/how-to-provide-automation-for-windows.md)  
 オートメーションを提供することことをお勧め、ウィンドウでオートメーション オブジェクトを使用できるようにして、環境に既に既製のオートメーション オブジェクトを提供しないときに説明します。 ツール ウィンドウおよびドキュメント ウィンドウのための自動化について説明します。  
  
 [オートメーション モデルを使用します。](../../extensibility/internals/using-the-automation-model.md)  
 Automation の消費者を取得する方法、初期のプロジェクト オートメーション オブジェクトを示す 2 つのコード例を提供します。  
  
 [構成および SelectedItem オブジェクトのための自動化](../../extensibility/internals/automation-for-configuration-and-selecteditem-objects.md)  
 Automation の構成と SelectedItems オブジェクトについてを説明します。  
  
## <a name="reference"></a>参照  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>  
 VSPackage が、DTE オートメーション オブジェクト モデルに参加する方法を示すコード サンプルを提供します。 パラメーター、戻り値、および選択した注釈の一覧を表示します。  
