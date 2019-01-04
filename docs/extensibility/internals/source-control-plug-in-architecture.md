---
title: ソース管理プラグイン アーキテクチャ |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, architecture
ms.assetid: 35351d4c-9414-409b-98fc-f2023e2426b7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ff2b19407ec63ea1227aba2affdad77f302dc129
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53868655"
---
# <a name="source-control-plug-in-architecture"></a>アーキテクチャのソース管理プラグイン
ソース管理サポートを追加することができます、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]統合開発環境 (IDE) を実装し、ソース管理プラグインをアタッチします。 IDE は、明確に定義されたソース管理プラグイン API を使用してプラグインのソース管理に接続します。 IDE では、ツールバーとメニュー コマンドで構成されるユーザー インターフェイス (UI) を提供することで、ソース管理システムのバージョン管理機能を公開します。 ソース管理プラグインは、ソース管理の機能を実装します。  
  
## <a name="source-control-plug-in-resources"></a>ソース管理プラグインのリソース  
 ソース管理のプラグインを作成およびバージョン管理アプリケーションを接続に役立つリソースを提供します、 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE。 ソース管理のプラグインに統合できるように、ソース管理プラグインによって実装する必要があります API 仕様が含まれています、 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE。 スケルトンのソース コントロール プラグイン デモの実装をソース管理プラグイン API に準拠して必要な基本的機能を実装するコード サンプル (C++ で記述された) も含まれています。  
  
 ソース管理プラグイン API 仕様では、関数、ソース管理プラグイン API に従って実装された一連の必要なソース管理 DLL を作成する場合は、好みの任意のソース管理システムを利用できます。  
  
## <a name="components"></a>コンポーネント  
 ソース コントロール アダプターのパッケージの図には、ソース管理プラグインでサポートされている関数の呼び出しにソース管理操作に対するユーザーの要求を変換する IDE のコンポーネントです。 これを実現するため、IDE とソース管理プラグインは、IDE およびプラグインの間で情報を前後へ渡すための効果的な ダイアログが必要です。 このダイアログ ボックスを行うには、同じ言語を読み上げますどちらもする必要があります。 このドキュメントに記載されているソース管理プラグイン API は、この exchange の一般的な用語です。  
  
 ![ソース コード管理アーキテクチャ ダイアグラム](../../extensibility/internals/media/vs_sccsdk_plug_in_arch.gif "vs_sccsdk_plug_in_arch")  
VS とソース管理の間の相互作用のプラグインを示すアーキテクチャ図  
  
 アーキテクチャの図に示すように、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]図では、VS shell とラベル付け、シェルは、ユーザーの実用的なプロジェクトとエディターやソリューション エクスプ ローラーなどの関連コンポーネントをホストします。 コントロール アダプターのソースのパッケージは、IDE とソース管理プラグイン間の対話を処理します。 コントロール アダプターのソースのパッケージは、独自のソース管理 UI を提供します。 開始し、ソース管理操作のスコープを定義するために、ユーザーが対話する最上位レベルの UI になります。  
  
 ソース管理プラグインは、独自の UI では、図に示すように 2 つの部分で構成されている可能性があることができます。 "ベンダー UI"というラベルの付いたボックスは、ソース管理プラグイン作成者として指定したカスタム ユーザー インターフェイス要素を表します。 ユーザーが、高度なソース管理操作を呼び出すと、ソース管理プラグインで直接表示されます。 "ヘルパー UI"というラベルの付いたボックスは、一連のソース管理プラグイン UI 機能、IDE から直接呼び出されます。 ソース管理プラグインは、IDE によって提供される特殊なコールバック関数を使用して IDE に UI に関連するメッセージを渡します。 ヘルパー UI には、IDE とのシームレスな統合が容易になります (多くの場合を使用すると、 **[詳細設定]** ボタン) より統一されたエンド ユーザー エクスペリエンスを提供します。  
  
 ソース管理プラグインに変更を加えることはできません、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]シェルし、その結果、ソース コントロール アダプターのパッケージまたはソースのいずれかを IDE によって提供される UI を制御します。 エンドユーザーの統合されたエクスペリエンスに影響するさまざまなソース管理プラグイン API 関数の実装によって提供される柔軟性の最大利用することにする必要があります。 ソース管理プラグイン API ドキュメントの参照セクションには、いくつか高度なソース管理プラグインの機能の情報が含まれます。 これらの機能を悪用するソース管理プラグインは、初期化中に、IDE の高度な機能を宣言する必要があり、各機能の特定の高度な機能を実装する必要があります。  
  
## <a name="see-also"></a>関連項目  
 [ソース管理プラグイン](../../extensibility/source-control-plug-ins.md)   
 [用語集](../../extensibility/source-control-plug-in-glossary.md)   
 [ソース管理プラグインの作成](../../extensibility/internals/creating-a-source-control-plug-in.md)