---
title: ドメイン ロールのプロパティ |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5a7bb18c-638e-45e8-9d79-9aa6a9e14b0e
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 6dc3f92bf1f9788f501b96540b35006ff112267b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47545985"
---
# <a name="properties-of-domain-roles"></a>ドメイン ロールのプロパティ
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[ドメイン ロールのプロパティの](https://docs.microsoft.com/visualstudio/modeling/properties-of-domain-roles)します。  
  
次の表に、プロパティは、役割をドメインに関連付けられます。 ドメイン ロールについては、次を参照してください。[理解のモデル、クラスとリレーションシップ](../modeling/understanding-models-classes-and-relationships.md)します。 これらのプロパティを使用する方法の詳細については、次を参照してください。[をカスタマイズすると、ドメイン固有言語を拡張する](../modeling/customizing-and-extending-a-domain-specific-language.md)します。  
  
|プロパティ|説明|既定値|  
|--------------|-----------------|-------------|  
|コレクション型|このロールが 0 の多重度を持つ場合.. * または 1.\*、このプロパティは、リンクのコレクションを格納するために使用するジェネリック型をカスタマイズします。|`(none)` - <xref:Microsoft.VisualStudio.Modeling.LinkedElementCollection%601> 使用します。|  
|カスタム属性|ここで指定した属性は、生成されたコード クラスに属性として追加されます。|\<なし >|  
|プロパティは、参照|場合`True`、リレーションシップの多重度が 0..1 または 1..1 の場合は、ロールのプロパティでユーザーが閲覧できる、**プロパティ**ウィンドウ。 プロパティには、リレーションシップ リンクの他の最後に、要素の名前が表示されます。|`True`|  
|プロパティをジェネレーターします。|場合`True`、このロールは、プログラム コード内のリレーションシップを走査に使用できるロールのプロパティが生成されます。 この設定した場合は false が場合、は、ドメイン リレーションシップの静的メソッドを使用してほど効率的でない方法でリレーションシップを移動できます。|`True`|  
|プロパティ ゲッター アクセス修飾子|生成されたプロパティのゲッター アクセス修飾子 (`public`、 `internal`、 `private`、 `protected`、または`protected internal`)。|`public`|  
|プロパティ Setter アクセス修飾子|生成されたプロパティの set アクセス操作子のアクセス修飾子 (`public`、 `internal`、 `private`、 `protected`、または`protected internal`)。|`public`|  
|複数要素の接続性|逆の役割を果たすことができるモデル要素の数 (`0..1`、 `1..1`、 `0..*`、または`1..*`)。 多重度が場合`0..*`または`1..*`、生成されたプロパティは、コレクションを表します。 それ以外の場合、生成されたプロパティが 1 つのモデル要素を表します。|リレーションシップの種類に依存し、これがリレーションシップのソースまたはターゲット ロールかどうか。|  
|名前|ドメイン ロールの名前。 このプロパティには、空白文字が含まれていないことができます。|このロールのロール プレーヤーのドメイン クラスの名前。|  
|コピーを伝達します。|`DoNotPropagateCopy` -コピーされたロール プレーヤーには、このリンクのコピーはありません。<br /><br /> `PropagateCopyToLinkOnly` -コピーのリンクは、既存の反対のロール プレーヤーを指します。<br /><br /> `PropagateCopyToLinkAndOppositeRolePlayer` -コピーのリンクは、反対のロール プレーヤーのコピーを指します。|`PropagateCopyToLinkAndOppositeRolePlayer` 埋め込みのソース ロール。<br /><br /> `DoNotPropagateCopy` その他のロール。<br /><br /> 詳細については、次を参照してください[コピー動作のカスタマイズ。](../modeling/customizing-copy-behavior.md)|  
|削除を伝達します。|`True` 関連のリンクが削除されたときにこの役割を果たす要素を削除します。|`True` 埋め込みのロールのターゲット。<br /><br /> `False` その他のロール。<br /><br /> 詳細については、次を参照してください。[削除の動作のカスタマイズ](../modeling/customizing-deletion-behavior.md)します。|  
|プロパティ名|ロール プレーヤーのコードで生成されるプロパティの名前。 この名前は、空白を含めることはできません。|このロールの 0 対 1 の場合は、反対のロールの名前または一対一の多重度。それ以外の場合、反対のロールの複数形の名前。|  
|ロール プレーヤー|リレーションシップでこの役割を果たすことができます、要素のドメイン クラス。 このプロパティは読み取り専用です。|このロールのロール プレーヤーのドメイン クラス。|  
|メモ|ドメインの役割に関連付けられている非公式のメモ。|\<なし >|  
|カテゴリ|生成されたプロパティを表示するカテゴリ、**プロパティ**生成されたデザイナーでウィンドウ。 かどうかは、このプロパティは空では、下に、生成されたプロパティが表示されます、 **Misc**カテゴリ|\<なし >|  
|説明|コードを文書化するために使用しては、生成されたデザイナーの UI で使用する説明。<br /><br /> ロール プレーヤー クラスに生成されたプロパティの Intellisense のツールヒントに説明が表示されます。|`Description for` *ロールの完全な名前*|  
|表示名|ドメインの役割を生成されたデザイナーに表示される名前です。|調整された Name プロパティの値をします。|  
|ヘルプ キーワード|ドメインの役割の F1 ヘルプのインデックスを作成するために使用する省略可能なキーワード。|\<なし >|  
|プロパティの表示名|生成されたロールのプロパティを生成されたデザイナーに表示される名前です。|プロパティ名のプロパティの調整された値。|  
  
> [!NOTE]
>  表示名の既定値を小文字の文字で前が実行され別の大文字の文字でないその後に各大文字の文字の前にスペースが挿入された関連付けられているプロパティの値に基づきます。  
  
## <a name="see-also"></a>関連項目  
 [ドメイン リレーションシップのプロパティ](../modeling/properties-of-domain-relationships.md)



