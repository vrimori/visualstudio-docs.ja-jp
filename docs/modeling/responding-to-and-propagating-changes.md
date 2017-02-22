---
title: "変更内容への対応および変更内容の反映 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ドメイン固有言語, イベント"
ms.assetid: fc2e9ac5-7a84-44ed-9945-94e45f89c227
caps.latest.revision: 24
caps.handback.revision: 24
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# 変更内容への対応および変更内容の反映
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

要素の作成削除または更新するとファイルデータベースまたは他のコンポーネントなどの外部リソースにモデルの他の部分に対する変更を反映するまたはコードを記述できます。  
  
## このセクションの内容  
 ガイドラインとして次の順序でこれらの方法を検討します :  
  
|手法|シナリオ|詳細情報|  
|--------|----------|----------|  
|計算されたドメインのプロパティを定義します。|値がモデル内の他のプロパティに基づいて計算されたドメインのプロパティ。  たとえば関連する要素の価格の合計価格があります。|[計算されると、カスタムの記憶域のプロパティ](../modeling/calculated-and-custom-storage-properties.md)|  
|カスタム ストレージのドメインのプロパティを定義します。|のまたは外部の他の部分に格納されているドメイン モデルのプロパティ。  たとえばモデルの式ツリーに文字列を解析します。|[計算されると、カスタムの記憶域のプロパティ](../modeling/calculated-and-custom-storage-properties.md)|  
|OnValueChanging と OnDeleting などのオーバーライドによってハンドラー|複数の要素を同期したままモデルと同期して外部値を保持します。<br /><br /> 定義した範囲に値を抑制します。<br /><br /> プロパティ値およびそのほかの直前の後に呼び出され変更します。  例外をスローして変更を終了できます。|[ドメイン プロパティ値変更ハンドラー](../modeling/domain-property-value-change-handlers.md)|  
|規則|変更が発生したトランザクションの最後の直前の実行のキューに規則を定義できます。  これらは戻す操作またはやり直し操作は実装されていません。  別の同期でストアの 1 部分を保持するために使用します。|[ルールには、モデル内の変更が反映されるまでください。](../modeling/rules-propagate-changes-within-the-model.md)|  
|イベントを保存します。|モデル ストアを追加したり要素またはリンクを削除するとそのプロパティの値を変更するなどのイベントについて通知します。  イベントは元に戻すとやり直すで実行されます。  ストアに更新した値にストアのイベントを使用します。|[イベント ハンドラーによって変更内容がモデル外に反映される](../modeling/event-handlers-propagate-changes-outside-the-model.md)|  
|.NET イベント|図形にマウス クリックなどの操作に応答するイベント ハンドラーがあります。  これらの各オブジェクトのイベントで登録する必要があります。  登録は InitializeInstanceResources のオーバーライドで一般に要素ごとにする必要があります。<br /><br /> これらのイベントは通常トランザクション外に発生します。|[方法: シェイプまたはデコレーターに対するクリック操作を受け取る](../Topic/How%20to:%20Intercept%20a%20Click%20on%20a%20Shape%20or%20Decorator.md)|  
|境界の規則|境界の規則は図形の境界を抑制するともに使用されます。|[BoundsRules によってシェイプの位置とサイズが制限される](../modeling/boundsrules-constrain-shape-location-and-size.md)|  
|選択規則|選択規則はユーザーが選択できる内容を抑制します。|[方法: 現在の選択項目を表示および制限する](../modeling/how-to-access-and-constrain-the-current-selection.md)|  
|OnAssocatedPropertyChanged|シャドウなどの図形と機能コネクタ矢印色と線の幅スタイル使用してモデル要素の状態を表示します。|[シェイプおよびコネクタの更新とモデルへの反映](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md)|  
  
## **規則および格納のイベントの比較**  
 通知者規則を変更すると変更がモデルに発生したときにイベントが実行されます。  
  
 規則は変更が発生しイベントが適用されたトランザクションのトランザクションで最後の変更がコミットされた後に適用されます。  
  
 ストアの外部のオブジェクト モデルとを同期するにはストア内の一貫性を維持するストアのイベントと規則を使用します。  
  
-   **カスタム規則を作成して**  抽象的な規則からカスタム規則をなどの派生クラスを作成します。  カスタム規則のフレームワークに通知する必要があります。  詳細については、「[ルールには、モデル内の変更が反映されるまでください。](../modeling/rules-propagate-changes-within-the-model.md)」を参照してください。  
  
-   イベントをサブスクライブする前に  **イベントをサブスクライブする**  イベント ハンドラーおよびデリゲートを作成します。  次にイベントのサブスクライブに <xref:Microsoft.VisualStudio.Modeling.Store.EventManagerDirectory%2A> のプロパティを使用します。  詳細については、「[イベント ハンドラーによって変更内容がモデル外に反映される](../modeling/event-handlers-propagate-changes-outside-the-model.md)」を参照してください。  
  
-   **元に戻すと** トランザクションを元に戻すとイベントが  **変更されますが** 規則は適用されません。  規則の値を変更しその変更を元に戻す場合値は元に戻す操作中に元の値にリセットされます。  イベントが発生すると元の値に値を返す必要があります。  transactons元の詳細については[方法: トランザクションを使用してモデルを更新する](../modeling/how-to-use-transactions-to-update-the-model.md) を参照してください。  
  
-   **イベント引数は規則とイベントの**  イベントと規則の両方  **に** モデルの変更した場合情報を含む `EventArgs` のパラメーターに渡されます。  
  
## 参照  
 [方法: シェイプまたはデコレーターに対するクリック操作を受け取る](../Topic/How%20to:%20Intercept%20a%20Click%20on%20a%20Shape%20or%20Decorator.md)   
 [ドメイン固有言語をカスタマイズするコードの記述](../modeling/writing-code-to-customise-a-domain-specific-language.md)