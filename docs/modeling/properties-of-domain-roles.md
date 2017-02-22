---
title: "ドメイン ロールのプロパティ | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5a7bb18c-638e-45e8-9d79-9aa6a9e14b0e
caps.latest.revision: 9
caps.handback.revision: 9
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# ドメイン ロールのプロパティ
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

次の表に示すプロパティはドメインのロールに関連付けられます。  ドメインのロールについては[モデル、クラス、およびリレーションシップについて](../modeling/understanding-models-classes-and-relationships.md) を参照してください。  これらのプロパティを使用する方法の詳細については[ドメイン固有言語のカスタマイズおよび拡張](../modeling/customizing-and-extending-a-domain-specific-language.md) を参照してください。  
  
|プロパティ|Description|既定値|  
|-----------|-----------------|---------|  
|コレクション型|このロールに 0 の多重度がある場合。\* または 1. \*このプロパティではリンクのコレクションを格納するために使用されるジェネリック型をカスタマイズします。|`(none)` <xref:Microsoft.VisualStudio.Modeling.LinkedElementCollection%601> が使用されます。|  
|カスタム属性|ここで指定する属性は生成されるコードのクラスに属性として追加されます。|なし|  
|プロパティはです Browsable|`True` は\[出力\] ウィンドウ ENT0ENT のユーザーによってリレーションシップの多重度が 0..1 または 1..1 場合プロパティに参照されます。  プロパティは関係のリンクの反対側の要素の名前が表示されます。|`True`|  
|ジェネレーター プロパティはです。|`True` がプログラム コードの関係を走査するために使用できるのはこのロールのプロパティに生成されます。  この false を設定するとドメイン リレーションシップの静的メソッドを使用するよりも効果的な方法でリレーションシップをスキャンできます。|`True`|  
|プロパティのアクセス修飾子|生成されたプロパティ \(`public``internal``private``protected`または `protected internal`\) のためのアクセス修飾子。|`public`|  
|プロパティの setter のアクセス修飾子|生成されたプロパティ \(`public``internal``private``protected`または\) `protected internal`setter のアクセス修飾子。|`public`|  
|Multiplicity|オブジェクトのロール \(`0..1``1..1``0..*`または `1..*`\) を持つことができるモデル要素の数。  多重度が `0..*` または `1..*` 場合生成されるプロパティはコレクションを表します ; それ以外の場合生成されるプロパティは一つのモデル要素を表します。|これはリレーションシップのソースまたはターゲットのロールであるかどうか関係の型によって異なります。|  
|名前|ドメインのロールの名前。  このプロパティを空白を含めることはできません。|このロールのロール プレーヤーのドメイン クラスの名前。|  
|伝達のコピー|\- ロール `DoNotPropagateCopy` プレーヤー コピーこのリンクのコピーはありません。<br /><br /> \- ロール `PropagateCopyToLinkOnly` プレーヤーのオブジェクトの既存リンクのコピーへのポインター。<br /><br /> \- ロール `PropagateCopyToLinkAndOppositeRolePlayer` プレーヤーのオブジェクトのコピーへのコピーへのポインター。|埋め込みアイテムのソースの各ロールの `PropagateCopyToLinkAndOppositeRolePlayer`。<br /><br /> 他のロールの `DoNotPropagateCopy`。<br /><br /> 詳細については、「[コピー動作のカスタマイズ](../modeling/customizing-copy-behavior.md)」を参照してください。|  
|伝達削除|関連リンクが削除されるときにこのロールを持つ要素を削除する `True`。|埋め込みロールのターゲットの `True`。<br /><br /> 他のロールの `False`。<br /><br /> 詳細については、「[削除動作のカスタマイズ](../modeling/customizing-deletion-behavior.md)」を参照してください。|  
|プロパティ名|ロール プレーヤーのコードで生成されたプロパティの名前。  この名前は空白を含めることはできません。|このロールにがゼロにある 1 または 1 対 1 の多重度対応するロール名 ; は対応するロールの名前 pluralized。|  
|プレーヤー ロール|このリレーションシップの役割を果たすことができる要素のドメイン クラス。  このプロパティは読み取り専用です。|このロールのロール プレーヤーのドメイン クラス。|  
|説明|ドメインのロールに関連付けられている単純に注意してください。|なし|  
|\[カテゴリ\]|生成されたプロパティが生成されるデザイナーの \[ENT0ENT\] ウィンドウで表示されるカテゴリ。  このプロパティが空の場合生成されるプロパティは  **その他**  のカテゴリに表示されます|なし|  
|Description|コードを作成するために使用され生成されるデザイナーの UI で使用される説明。<br /><br /> ついてはクラスの生成されたプロパティの Intellisense のロール プレーヤーのツールヒントに表示されます。|`Description for`  *ロールの完全名*|  
|\[表示名\]|ドメインのロールに対して生成されたデザイナーに表示される名前。|名前のプロパティの変更された値。|  
|ヘルプ キーワード|ドメインのロールで F1 ヘルプにインデックスを付けるために使用される省略可能なキーワード。|なし|  
|プロパティの表示名|生成されたロールのプロパティに対して生成されたデザイナーに表示される名前。|プロパティ名のプロパティの変更された値。|  
  
> [!NOTE]
>  表示名の既定値は関連付けられているプロパティ値が前に付いた小文字に別の英大文字が続かないしそれぞれの大文字の前の空白を挿入して基づいています。  
  
## 参照  
 [ドメイン リレーションシップのプロパティ](../modeling/properties-of-domain-relationships.md)