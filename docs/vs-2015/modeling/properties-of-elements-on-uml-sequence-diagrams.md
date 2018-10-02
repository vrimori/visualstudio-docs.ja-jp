---
title: シーケンス図の uml 要素のプロパティ |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.teamarch.sequencediagram.combinedfragment.properties
- vs.teamarch.sequencediagram.shapes.properties
helpviewer_keywords:
- UML sequence diagrams, properties
- sequence diagrams, properties
ms.assetid: 475c10f3-a2d2-4a1e-b366-dc28997d437e
caps.latest.revision: 22
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: b1f83999f3859583c4429ff3bf19482f01d90546
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47533399"
---
# <a name="properties-of-elements-on-uml-sequence-diagrams"></a>UML シーケンス図の要素のプロパティ
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[UML 要素のプロパティのシーケンス図](https://docs.microsoft.com/visualstudio/modeling/properties-of-elements-on-uml-sequence-diagrams)します。  
  
UML シーケンス図では、図の各要素にプロパティが存在します。 要素のプロパティを表示するには、図、または要素を右クリックして**UML モデル エクスプ ローラー**し**プロパティ**します。 プロパティが表示されます、**プロパティ**ウィンドウ。  
  
> [!NOTE]
>  このトピックでは、UML シーケンス図の要素のプロパティについて説明します。 UML シーケンス図を読み取る方法の詳細については、次を参照してください。 [UML シーケンス図: リファレンス](../modeling/uml-sequence-diagrams-reference.md)します。 UML シーケンス図を描画する方法の詳細については、次を参照してください。 [UML シーケンス図: ガイドライン](../modeling/uml-sequence-diagrams-guidelines.md)します。  
  
## <a name="properties-of-elements"></a>要素のプロパティ  
  
|プロパティ|既定値|要素|説明|  
|--------------|-------------|-------------|-----------------|  
|**Name**|既定名|すべて|要素を指定します。|  
|**修飾名**|Package :: Name|すべて|要素を一意に識別します。 要素を格納するパッケージの修飾名が先頭につきます。|  
|**作業項目**|関連付けなし|すべて|この要素に関連付けられている作業項目の数。 作業項目に関連付けるを参照してください。[モデル要素をリンクし、作業項目](../modeling/link-model-elements-and-work-items.md)します。|  
|**説明**|(空白)|すべて|ここに、項目に関する一般的なメモを作成できます。|  
|**色**|(要素の型の既定値)|生存線、メッセージ|シェイプの色。 これは、図形が表示する要素ではなく、図形のプロパティです。|  
|**Type**|(空白)|生存線|生存線を表すインスタンスの型。<br /><br /> 生存線のヘッダーに表示される参照シンボルがある場合は、このクラスまたはインターフェイスは UML モデル エクスプローラーで個別に存在していて、クラス図に表示することができます。|  
|**アクター**|False|生存線|生存線は、この図の対象となるコンポーネントに対して外部となるユーザー、デバイス、またはソフトウェア コンポーネントを表すかどうかを示します。|  
|**種類**|**完全な**-送信者と受信者の両方を持つメッセージ。<br /><br /> **見つかった**-を指定されていない送信者を持つメッセージ。<br /><br /> **失われた**-指定されていない受信者を持つメッセージ。|メッセージ|メッセージのどちらの終端を生存線にアタッチするかを示します。<br /><br /> このプロパティは変更できません。 これは、メッセージを作成するときに設定されます。|  
|**並べ替え**|**AsynchCall** -非同期メッセージ。<br /><br /> **SynchCall** -同期メッセージ。<br /><br /> **返信**-同期メッセージの戻り値の一部です。<br /><br /> **CreateMessage** -インスタンスの生成メッセージ。|メッセージ|メッセージの種類。 このプロパティは変更できません。 メッセージの作成に使用するツールによって決定されます。|  
|**操作**|(空)|メッセージ|受信側の生存線のメッセージによって呼び出されるメソッド。<br /><br /> 受信側の生存線が、インターフェイスまたはクラスにリンクされている場合にのみ表示されます。|  
|**参照するには**|シーケンス図|相互作用使用|この相互作用使用によって呼び出されるシーケンス図。|  
|**相互作用演算子**|設定を使用した場合、**ブロックの挿入**コマンド|結合フラグメント|このフラグメントまたはフラグメントのコレクションが表す演算子。|  
|**ガード**|(空)|結合フラグメント内の相互作用オペランド|ガードが True でない限り、フラグメント内のシーケンスは発生しません。<br /><br /> 結合フラグメントの一番上のフラグメントを選択するには、フラグメントのタイトルの下をクリックします。|  
|**Min、Max**|(制限なし)|ループ結合フラグメント|ループ実行回数の最小値と最大数。|  
|**メッセージ**|(空)|検討し、<br /><br /> 結合フラグメントを無視します。|このフラグメント内で検討または無視するメッセージ。|  
  
## <a name="see-also"></a>関連項目  
 [UML シーケンス図: リファレンス](../modeling/uml-sequence-diagrams-reference.md)   
 [UML シーケンス図: ガイドライン](../modeling/uml-sequence-diagrams-guidelines.md)   
 [UML シーケンス図のフラグメントを使用した制御フローの記述](../modeling/describe-control-flow-with-fragments-on-uml-sequence-diagrams.md)



