---
title: InvokeMethod アクティビティ デザイナー |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.Activities.Statements.InvokeMethod.UI
ms.assetid: 15e6efdc-52ca-46d8-9c5e-063f7c8265a6
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 27be9bc979ba1f3e86996aaf913502ca80142ebd
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49252968"
---
# <a name="invokemethod-activity-designer"></a>InvokeMethod アクティビティ デザイナー
**InvokeMethod**を作成および構成デザイナーを使用する<xref:System.Activities.Statements.InvokeMethod>アクティビティ。  
  
## <a name="the-invokemethod-activity"></a>InvokeMethod アクティビティ  
 <xref:System.Activities.Statements.InvokeMethod> は、指定されたオブジェクトまたは型のパブリック メソッドを呼び出します。  
  
### <a name="using-the-invokemethod-activity-designer"></a>InvokeMethod アクティビティ デザイナーの使用  
 **InvokeMethod**アクティビティ デザイナーが記載されて、**プリミティブ**のカテゴリ、**ツールボックス**をクリックしてアクセスする、**ツールボックス**タブ[!INCLUDE[wfd2](../includes/wfd2-md.md)](または、選択**ツールバー**から、**ビュー**メニューのまたは CRTL + ALT + X)。  
  
 **InvokeMethod**からアクティビティ デザイナーをドラッグすることができます、**ツールボックス**ドロップ、[!INCLUDE[wfd2](../includes/wfd2-md.md)]サーフェス場所、アクティビティを通常配置など内、<xref:System.Activities.Statements.Sequence>します。 この操作により、InvokeMethod という既定の <xref:System.Activities.Statements.InvokeMethod> を持つ <xref:System.Activities.Activity.DisplayName%2A> アクティビティが作成されます。 <xref:System.Activities.Activity.DisplayName%2A>のヘッダーで編集できる、 **InvokeMethod**アクティビティ デザイナーまたは、 **DisplayName**プロパティ グリッドのボックスです。  
  
### <a name="the-invokemethod-properties"></a>InvokeMethod プロパティ  
 次の表に、<xref:System.Activities.Statements.InvokeMethod> のプロパティと、デザイナーでのその使用方法を示します。 これらのプロパティは、プロパティ グリッドで編集できます。また、その一部は[!INCLUDE[wfd2](../includes/wfd2-md.md)]のデザイナー画面で編集できます。  
  
|プロパティ名|必須|使用方法|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.InvokeMethod> アクティビティの表示名。 既定値は InvokeMethod です。<br /><br /> <xref:System.Activities.Activity.DisplayName%2A> は必須ではありませんが、使用することをお勧めします。|  
|<xref:System.Activities.Statements.InvokeMethod.MethodName%2A>|True|アクティビティの実行時に呼び出すメソッドの名前。 呼び出されたメソッドとして宣言する必要があります**パブリック**します。 このプロパティは、デザイナー画面で設定することもできます。 これは必須プロパティです。|  
|<xref:System.Activities.Statements.InvokeMethod.Parameters%2A>|False|呼び出されたメソッドのパラメーター コレクション。 パラメーターは、メソッド シグネチャ内で出現する順序でコレクションに追加する必要があります。 プロパティ グリッドで、省略記号ボタンをクリックします。、**パラメーター**フィールドが表示されます、**パラメーター**ダイアログ ボックスを使用するこのプロパティを設定できます。 をクリックして、**引数の作成**パラメーターを追加するボタンをクリックします。|  
|<xref:System.Activities.Statements.InvokeMethod.Result%2A>|False|メソッド呼び出しの戻り値。|  
|<xref:System.Activities.Statements.InvokeMethod.RunAsynchronously%2A>|True|メソッドが非同期で呼び出されるかどうかを指定します。 既定値は**False**します。|  
|<xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>|False|呼び出すメソッドを格納するオブジェクト。 このプロパティは、デザイナー画面で設定することもできます。<br /><br /> <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> および <xref:System.Activities.Statements.InvokeMethod.TargetType%2A> のいずれかを設定する必要があります。|  
|<xref:System.Activities.Statements.InvokeMethod.TargetType%2A>|False|<xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> の型。 このプロパティは、デザイナー画面で編集できます。 このプロパティは、メソッド呼び出しが静的である場合にのみ設定する必要があります。|  
  
 C# としてパラメーターを渡す**アウト**パラメーター (たとえば、`Method1(out myParam)),`を使用する必要があります**OutArgument**の代わりに**InOutArgument**  
  
 呼ばれる引数を持つメソッド**TargetObject**または**結果**を使用して呼び出すことはできません、<xref:System.Activities.Statements.InvokeMethod>アクティビティ。 これは、<xref:System.Activities.Statements.InvokeMethod> アクティビティによって <xref:System.Activities.Statements.InvokeMethod.GenericTypeArguments%2A>、<xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>、および <xref:System.Activities.Statements.InvokeMethod.Result%2A> が <xref:System.Activities.Activity.CacheMetadata%2A> に登録されるためです。  
  
 <xref:System.Activities.Activity.CacheMetadata%2A> にパラメーターを登録するアルゴリズムは次のとおりです。  
  
1.  <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> 引数を登録します。  
  
2.  <xref:System.Activities.Statements.InvokeMethod.Result%2A> 引数を登録します。  
  
3.  <xref:System.Activities.Statements.InvokeMethod.Parameters%2A> コレクションを繰り返し処理し、各引数を登録します。  
  
 結果の例外の種類は <xref:System.Activities.InvalidWorkflowException> となり、メッセージの内容は、"'InvokeMethod': 名前が 'TargetObject' の変数 RuntimeArgument または DelegateArgument は既に存在します" となります。 名前は、環境スコープ内で一意であることが必要です。  
  
 この制限は、<xref:System.Activities.Statements.InvokeMethod.TargetType%2A> および <xref:System.Activities.Statements.InvokeMethod.RunAsynchronously%2A> には適用されません。これらはワークフロー引数ではなく、したがって、<xref:System.Activities.Statements.InvokeMethod.GenericTypeArguments%2A> メソッド内の <xref:System.Activities.Statements.InvokeMethod> アクティビティの<xref:System.Activities.Activity.CacheMetadata%2A> コレクションに登録されないためです。  
  
## <a name="see-also"></a>関連項目  
 [プリミティブ](../workflow-designer/primitives-activity-designers.md)   
 [割り当てる](../workflow-designer/assign-activity-designer.md)   
 [遅延](../workflow-designer/delay-activity-designer.md)   
 [WriteLine](../workflow-designer/writeline-activity-designer.md)