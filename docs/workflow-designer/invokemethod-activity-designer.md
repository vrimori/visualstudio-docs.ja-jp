---
title: ワークフロー デザイナーで InvokeMethod アクティビティ デザイナー
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
f1_keywords:
- System.Activities.Statements.InvokeMethod.UI
ms.assetid: 15e6efdc-52ca-46d8-9c5e-063f7c8265a6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7f7cfc820f6f4d3596c932760442371bab294a05
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54999770"
---
# <a name="invokemethod-activity-designer"></a>InvokeMethod アクティビティ デザイナー

**InvokeMethod**を作成および構成デザイナーを使用する<xref:System.Activities.Statements.InvokeMethod>アクティビティ。

## <a name="the-invokemethod-activity"></a>InvokeMethod アクティビティ

<xref:System.Activities.Statements.InvokeMethod> は、指定されたオブジェクトまたは型のパブリック メソッドを呼び出します。

### <a name="use-the-invokemethod-activity-designer"></a>InvokeMethod アクティビティ デザイナーを使用します。

アクセス、 **InvokeMethod**内のアクティビティ デザイナー、**プリミティブ**のカテゴリ、**ツールボックス**します。 **InvokeMethod**からアクティビティ デザイナーをドラッグすることができます、**ツールボックス**がずっと、アクティビティを通常配置など内に、ワークフロー デザイナー画面にドロップし、<xref:System.Activities.Statements.Sequence>します。 アクティビティ デザイナーをドロップを作成、 <xref:System.Activities.Statements.InvokeMethod> 、既定値は、アクティビティ<xref:System.Activities.Activity.DisplayName%2A>InvokeMethod の。 <xref:System.Activities.Activity.DisplayName%2A>のヘッダーで編集できる、 **InvokeMethod**アクティビティ デザイナーまたは、 **DisplayName**プロパティ グリッドのボックスです。

### <a name="the-invokemethod-properties"></a>InvokeMethod プロパティ

次の表は、<xref:System.Activities.Statements.InvokeMethod>プロパティと、デザイナーでの使用方法について説明します。 これらのプロパティは、プロパティ グリッドで編集できるし、一部は、ワークフロー デザイナー画面で編集できます。

|プロパティ名|必須|使用方法|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.InvokeMethod> アクティビティの表示名。 既定値は InvokeMethod です。<br /><br /> ただし、<xref:System.Activities.Activity.DisplayName%2A>必須ではありませんいずれかを使用することをお勧めします。|
|<xref:System.Activities.Statements.InvokeMethod.MethodName%2A>|True|アクティビティの実行時に呼び出すメソッドの名前。 呼び出されたメソッドとして宣言する必要があります**パブリック**します。 このプロパティは、デザイナー画面で編集でき、必須です。|
|<xref:System.Activities.Statements.InvokeMethod.Parameters%2A>|False|呼び出されたメソッドのパラメーター コレクション。 パラメーターは、メソッド シグネチャ内で出現する順序でコレクションに追加する必要があります。 表示する、**パラメーター** 、このプロパティを設定するダイアログで、省略記号ボタンをクリックして、**パラメーター**プロパティ グリッドのフィールド。 をクリックして、**引数の作成**パラメーターを追加するボタンをクリックします。|
|<xref:System.Activities.Statements.InvokeMethod.Result%2A>|False|メソッド呼び出しの戻り値。|
|<xref:System.Activities.Statements.InvokeMethod.RunAsynchronously%2A>|True|メソッドが非同期で呼び出されるかどうかを指定します。 既定値は**False**します。|
|<xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>|False|呼び出すメソッドを格納するオブジェクト。 このプロパティは、デザイナー画面で設定することもできます。<br /><br /> <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> および <xref:System.Activities.Statements.InvokeMethod.TargetType%2A> のいずれかを設定する必要があります。|
|<xref:System.Activities.Statements.InvokeMethod.TargetType%2A>|False|<xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> の型。 このプロパティは、デザイナー画面で編集できます。 このプロパティは、メソッド呼び出しが静的である場合にのみ設定する必要があります。|

C# としてパラメーターを渡す**アウト**パラメーター (たとえば、`Method1(out myParam))`を使用して、 **OutArgument**の代わりに**InOutArgument**

呼ばれる引数を持つメソッド**TargetObject**または**結果**を使用して呼び出すことはできません、<xref:System.Activities.Statements.InvokeMethod>アクティビティ。 これは、<xref:System.Activities.Statements.InvokeMethod> アクティビティによって <xref:System.Activities.Statements.InvokeMethod.GenericTypeArguments%2A>、<xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>、および <xref:System.Activities.Statements.InvokeMethod.Result%2A> が <xref:System.Activities.Activity.CacheMetadata%2A> に登録されるためです。

<xref:System.Activities.Activity.CacheMetadata%2A> にパラメーターを登録するアルゴリズムは次のとおりです。

1.  <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> 引数を登録します。

2.  <xref:System.Activities.Statements.InvokeMethod.Result%2A> 引数を登録します。

3.  <xref:System.Activities.Statements.InvokeMethod.Parameters%2A> コレクションを繰り返し処理し、各引数を登録します。

型の結果の例外は、<xref:System.Activities.InvalidWorkflowException>次のメッセージ。' InvokeMethod':名前が 'TargetObject' の変数 RuntimeArgument または DelegateArgument を既にが存在します。 名前は、環境スコープ内で一意であることが必要です。

この制限には適用されません<xref:System.Activities.Statements.InvokeMethod.TargetType%2A>と<xref:System.Activities.Statements.InvokeMethod.RunAsynchronously%2A>します。 ワークフローの引数がないに登録されていないため、<xref:System.Activities.Statements.InvokeMethod.GenericTypeArguments%2A>のコレクション、<xref:System.Activities.Statements.InvokeMethod>内のアクティビティ、<xref:System.Activities.Activity.CacheMetadata%2A>メソッド。

## <a name="see-also"></a>関連項目

- [Primitives](../workflow-designer/primitives-activity-designers.md)
- [Assign](../workflow-designer/assign-activity-designer.md)
- [Delay](../workflow-designer/delay-activity-designer.md)
- [WriteLine](../workflow-designer/writeline-activity-designer.md)