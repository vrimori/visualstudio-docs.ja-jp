---
title: 'UML コンポーネント図: リファレンス |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.teamarch.componentdiagram.diagram
- vs.teamarch.componentdiagram.toolbox
- vs.teamarch.UMLModelExplorer.componentdiagram
helpviewer_keywords:
- UML diagrams, component
- diagrams - modeling, component
- diagrams - modeling, UML component
- UML, component diagrams
- component diagrams
ms.assetid: 5eddff6a-892a-4c3c-9278-687ac1eccc50
caps.latest.revision: 38
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: b99188aa069a830d17e31733ad20b0ae727d63f9
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49206742"
---
# <a name="uml-component-diagrams-reference"></a>UML コンポーネント図: リファレンス
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio で、*コンポーネント図*ソフトウェア システムの設計の部分を示しています。 コンポーネント図は、システムの大まかな構造と、これらのパートがインターフェイスを介して提供および使用するサービス動作を視覚化するのに役立ちます。 UML コンポーネント図を作成する、**アーキテクチャ** メニューのをクリックして**新しい UML またはレイヤー図**します。  
  
 この機能をサポートする Visual Studio のバージョンを確認するには、「 [アーキテクチャ ツールとモデリング ツールのバージョン サポート](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)」を参照してください。  
  
 コンポーネント図を使用して、任意の言語またはスタイルで実装されている設計を記述できます。 必要になるのは、制限された入力および出力のセットを介して設計の他のパートと対話するパートを識別することだけです。 コンポーネントは任意のスケールで記述し、任意の方法で相互接続することができます。  
  
 コンポーネント図を設計プロセスで使用する方法の詳細については、次を参照してください。 [、アプリケーションのアーキテクチャをモデル化](../modeling/model-your-app-s-architecture.md)します。  
  
> [!NOTE]
>  このトピックでは、コンポーネント図で使用できる要素について説明します。 コンポーネント図を描画する方法について詳細を参照してください。 [UML コンポーネント図: ガイドライン](../modeling/uml-component-diagrams-guidelines.md)します。 一般にモデリング図を描画する方法の詳細については、次を参照してください。[編集 UML モデルと図](../modeling/edit-uml-models-and-diagrams.md)します。  
  
## <a name="reading-component-diagrams"></a>コンポーネント図の解説  
 コンポーネント図で使用できる要素とその主要なプロパティを次の表に示します。 要素のプロパティの完全な一覧は、次を参照してください。 [UML コンポーネント図の要素のプロパティ](../modeling/properties-of-elements-on-uml-component-diagrams.md)します。  
  
 ![コンポーネント図で使用される要素](../modeling/media/uml-compovreading.png "UML_CompOvReading")  
  
|**図形**|**要素**|**説明と主要なプロパティ**|  
|---------------|-----------------|-----------------------------------------|  
|1|**コンポーネント**|再利用可能なシステム機能の一部分。 コンポーネントは、インターフェイスを介してビヘイビアーを提供および使用します。他のコンポーネントを使用する場合もあります。<br /><br /> 展開/折りたたみコントロール (9) を使用して、コンポーネントの内部パートの非表示/表示を切り替えることができます。<br /><br /> コンポーネントは、一種のクラスです。<br /><br /> -   **直接インスタンス化**します。 true (既定値) の場合、コンポーネントは設計上のアーティファクトとしてのみ存在します。 実行時には、そのパートのみが存在します。|  
|2|**提供インターフェイス ポート**|コンポーネントが実装し、他のコンポーネントまたは外部システムが使用できるメッセージまたは呼び出しのグループを表します。 ポートはコンポーネントのプロパティであり、型としてインターフェイスが指定されます。|  
|3|**要求インターフェイス ポート**|コンポーネントが他のコンポーネントまたは外部システムに送信するメッセージまたは呼び出しのグループを表します。 コンポーネントは、少なくともこれらの操作を提供する他のコンポーネントと連結されるように設計されています。 ポートには、型としてインターフェイスが指定されます。|  
|4|**依存関係**|あるコンポーネントの要求インターフェイスを他のコンポーネントの提供インターフェイスによって満たせることを示します。<br /><br /> 依存関係はモデル要素間でより汎用的に使用することもでき、これによって、あるコンポーネントの設計が他のコンポーネントの設計に依存していることを示せます。|  
|5|**一部**|コンポーネントの属性であり、通常、型として別のコンポーネントが指定されます。 パートは、親コンポーネントの内部設計で使用されます。 パートは、親コンポーネント内に入れ子にされた項目としてグラフィカルに表示されます。<br /><br /> 既存のコンポーネント型のパートを生成するには、UML モデル エクスプローラーから所有者コンポーネントにコンポーネントをドラッグします。<br /><br /> 新しい型の一部を作成する をクリックして、**コンポーネント**ツールし、所有者部分をクリックします。<br /><br /> たとえば、`Car` というコンポーネントは、`engine:CarEngine`、`backLeft:Wheel`、`frontRight:Wheel` などのパートを持ちます。<br /><br /> 複数のパートが同じ型を持つことがあり、また複数の異なるコンポーネントが同じ型のパートを持つこともあります。<br /><br /> -   **型**します。 パートの型であり、モデル内の他の場所で定義されています。 通常、型として別のコンポーネントが指定されます。<br />-   **多重度**します。 既定値は 1 です。 設定した**0..1**部品が値を持つことを示す**null**、 **\*** 部分が指定された型のインスタンスのコレクションであることを示すまたは任意の式に数値の範囲を評価できます。|  
|6|**パート アセンブリ**|あるパートの要求インターフェイス ポートと別のパートの提供インターフェイス ポートの間の接続。 パート アセンブリの実装は、コンポーネントによって異なる場合があります。 接続されているパートは、同じ親コンポーネントを持つ必要があります。|  
|7|**委任**|ポートをコンポーネントのいずれかのパートのインターフェイスにリンクします。 コンポーネントに送信されたメッセージがそのパートによって処理されること、またはそのパートから送信されたメッセージが親コンポーネントを経由して送信されることを示します。|  
|(表示されていません)|**汎化**|あるコンポーネントが別のコンポーネントを継承することを示します。 パートおよびインターフェイスが継承されます。|  
|9|折りたたみ/展開コントロール|これを使用して、コンポーネントの内部パートの非表示/表示を切り替えます。|  
|(表示されていません)|**コメント**|追加メモ。 任意の数の図の要素にコメントをリンクするにを使用して、**コネクタ**ツール。|  
  
## <a name="see-also"></a>関連項目  
 [UML モデルおよびダイアグラムを編集します。](../modeling/edit-uml-models-and-diagrams.md)   
 [UML コンポーネント図: ガイドライン](../modeling/uml-component-diagrams-guidelines.md)   
 [開発中にシステムを検証します。](../modeling/validate-your-system-during-development.md)   
 [UML ユース ケース図: リファレンス](../modeling/uml-use-case-diagrams-reference.md)   
 [UML クラス図: リファレンス](../modeling/uml-class-diagrams-reference.md)   
 [UML アクティビティ図: リファレンス](../modeling/uml-activity-diagrams-reference.md)   
 [UML シーケンス図: リファレンス](../modeling/uml-sequence-diagrams-reference.md)



