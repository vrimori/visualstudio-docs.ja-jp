---
title: "ソース管理プラグイン アーキテクチャ |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: source control plug-ins, architecture
ms.assetid: 35351d4c-9414-409b-98fc-f2023e2426b7
caps.latest.revision: "24"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e0cde4ca360aa0059abcbe0b64d63b4a94e85d78
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="source-control-plug-in-architecture"></a>ソース管理プラグイン アーキテクチャ
ソース コントロールのサポートを追加することができます、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]統合開発環境 (IDE) で実装して、ソース管理プラグインをアタッチします。 IDE は、適切に定義されたソース管理プラグイン API を使用してプラグイン ソース管理に接続します。 IDE では、ツールバーとメニュー コマンドで構成されるユーザー インターフェイス (UI) を提供することにより、ソース管理システムのバージョン コントロール機能を公開します。 ソース管理プラグインでは、ソース管理機能を実装します。  
  
## <a name="source-control-plug-in-resources"></a>ソース管理プラグイン リソース  
 ソース管理プラグインを作成し、バージョン管理アプリケーションを接続するためにリソースを提供する、 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE です。 ソース管理プラグインに統合できるように、ソース管理プラグインで実装される必要がある API 仕様が含まれています、 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE です。 スケルトン ソース プラグイン示すのコントロールの実装、ソース管理プラグイン API に準拠している重要な機能を実装するコード サンプル (C++ で記述された) も含まれています。  
  
 ソース管理プラグイン API 仕様では、関数、ソース管理プラグイン API に従って実装された一連の必要なソース管理 DLL を作成する場合に、選択した任意のソース管理システムを利用できます。  
  
## <a name="components"></a>コンポーネント  
 ダイアグラムでソース管理アダプターのパッケージは、ソース管理プラグインでサポートされている関数呼び出しにソース管理操作のユーザーの要求を変換する IDE のコンポーネントです。 これを実現するには、IDE とソース管理プラグインは、IDE およびプラグインの間で情報を行ったり来たり経過する効果的なダイアログになければなりません。 このダイアログ ボックスを行うには、同じ言語を使用、どちらもする必要があります。 このドキュメントに記載されているソース管理プラグイン API とは、この exchange の一般的な用語です。  
  
 ![ソース コード管理アーキテクチャ ダイアグラム](../../extensibility/internals/media/vs_sccsdk_plug_in_arch.gif "vs_sccsdk_plug_in_arch")  
VS およびソース管理の間の相互作用をプラグインを示すアーキテクチャ図  
  
 アーキテクチャの図に示すように、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]シェル、というラベルが付いたとして VS shell の図では、ユーザーの実用的なプロジェクトとエディターやソリューション エクスプ ローラーなどの関連コンポーネントをホストします。 ソース管理アダプター パッケージは、IDE とソース管理プラグイン間の対話を処理します。 ソース管理アダプター パッケージは、独自のソース管理 UI を提供します。 開始し、ソース管理操作のスコープを定義するために、ユーザーが対話する最上位レベルの UI です。  
  
 ソース管理プラグインは、独自の UI では、図に示すように 2 つの部分で構成されている可能性がありますを持つことができます。 "ベンダー UI"というラベルの付いたボックスは、ソース管理プラグイン作成者として提供するカスタム ユーザー インターフェイス要素を表します。 ユーザーが高度なソース管理操作を呼び出す場合は、ソース管理プラグインによって直接はこれらが表示されます。 "ヘルパー UI"というラベルの付いたボックスは、ソース管理プラグイン UI の機能は直接、IDE によって呼び出されるのセットです。 ソース管理プラグインは、IDE によって提供される特殊なコールバック関数を使用して IDE に UI に関連するメッセージを渡します。 ヘルパー UI には、IDE とのシームレスな統合が容易になります (多くの場合を使用すると、 **[詳細設定]**ボタンをクリック) し、したがってより統合されたエンド ユーザー エクスペリエンスを提供します。  
  
 ソース管理プラグインに変更を加えることはできません、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]シェルし、その結果、ソース管理アダプター パッケージまたはソースのいずれかを制御する、IDE によって提供される UI。 これにより、エンドユーザーの統合された環境に影響する、さまざまなソース管理プラグイン API 関数の実装で提供される柔軟性を最大限に使用する必要があるためです。 ソース管理プラグイン API のドキュメントのリファレンスのセクションには、高度なソース管理プラグイン機能の情報が含まれます。 これらの機能を利用するには、ソース管理プラグインは、初期化中に、その高度な機能を IDE を宣言する必要があり、各機能の特定の高度な関数を実装する必要があります。  
  
## <a name="see-also"></a>関連項目  
 [ソース管理プラグイン](../../extensibility/source-control-plug-ins.md)   
 [用語集](../../extensibility/source-control-plug-in-glossary.md)   
 [ソース管理プラグインの作成](../../extensibility/internals/creating-a-source-control-plug-in.md)