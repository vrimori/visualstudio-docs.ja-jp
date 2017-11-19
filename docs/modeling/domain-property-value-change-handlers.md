---
title: "ドメイン プロパティ値変更ハンドラー |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Domain-Specific Language, overriding event handlers
ms.assetid: 96d8f392-045e-4bc5-b165-fbaa470a3e16
caps.latest.revision: "24"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: effe18c4b4d363bd7fa4cbed29ddf254c85aac31
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="domain-property-value-change-handlers"></a>ドメイン プロパティ値変更ハンドラー
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ドメイン固有言語で、ドメイン プロパティの値が変わると、ドメイン プロパティ ハンドラーで `OnValueChanging()` メソッドおよび `OnValueChanged()` メソッドが呼び出されます。 変更に応答するために、これらのメソッドをオーバーライドできます。  
  
## <a name="overriding-the-property-handler-methods"></a>プロパティ ハンドラー メソッドのオーバーライド  
 ドメイン固有言語の各ドメイン プロパティは親のドメイン クラス内で入れ子になっているクラスにより処理されます。 その名前が、形式に従って*PropertyName*PropertyHandler です。 ファイル内のこのプロパティ ハンドラー クラスを検査する**Dsl\Generated Code\DomainClasses.cs**です。 このクラスで、`OnValueChanging()` は値が変更される直前に呼び出され、`OnValueChanged()` は値が変更された直後に呼び出されます。  
  
 たとえば、という名前のドメイン クラス`Comment`という名前の文字列ドメインのプロパティを持つ`Text`および名前付き整数のプロパティ`TextLengthCount`です。 発生する`TextLengthCount`の長さを格納するには、常に、`Text`文字列、Dsl プロジェクト内の別のファイルに次のコードを記述する可能性があります。  
  
```  
// Domain Class "Comment":  
public partial class Comment   
{  
  // Domain Property "Text":  
  partial class TextPropertyHandler  
  {  
    protected override void OnValueChanging(CommentBase element, string oldValue, string newValue)  
    {  
      base.OnValueChanging(element, oldValue, newValue);  
  
      // To update values outside the Store, write code here.  
  
      // Let the transaction manager handle undo:  
      Store store = element.Store;  
      if (store.InUndoRedoOrRollback || store.InSerializationTransaction) return;  
  
      // Update values in the Store:  
      this.TextLengthCount = newValue.Length;  
    }  
  }  
}  
  
```  
  
 プロパティ ハンドラーについては次の点に注意してください。  
  
-   プロパティ ハンドラー メソッドは、ユーザーがドメイン プロパティに変更を加えたときと、プログラム コードがプロパティに別の値を割り当てたときの両方で呼び出されます。  
  
-   メソッドは値が実際に変更された時点でのみ呼び出されます。 プログラム コードにより現在の値に等しい値が代入された場合、ハンドラーは呼び出されません。  
  
-   計算されるドメイン プロパティおよびカスタム ストレージ ドメイン プロパティには OnValueChanged メソッドおよび OnValueChanging メソッドがありません。  
  
-   変更ハンドラーを使用して新しい値を変更することはできません。 たとえば、値を特定の範囲に制限する場合などは、`ChangeRule` を定義します。  
  
-   リレーションシップのロールを表すプロパティに変更ハンドラーを追加することはできません。 その代わり、リレーションシップ クラス上で `AddRule` および `DeleteRule` を定義します。 これらの規則は、リンクが作成または変更されるとトリガーされます。 詳細については、次を参照してください。[ルール反映されるまで変更内で、モデル](../modeling/rules-propagate-changes-within-the-model.md)です。  
  
### <a name="changes-in-and-out-of-the-store"></a>ストア内外の変更  
 プロパティ ハンドラー メソッドは変更を開始したトランザクションの内部で呼び出されます。 したがって、新しいトランザクションを開かずに、ストア内でより多くの変更を加えることができます。 変更により追加のハンドラーが呼び出される場合があります。  
  
 トランザクションが元に戻されている場合、再実行されている場合、またはロールバックされている場合は、ストア内に変更を加えること、つまり、モデル要素、リレーションシップ、図形、コネクタ、図、またはそれらのプロパティに変更を加えることはできません。  
  
 さらに、モデルがファイルから読み込まれているときは、通常、値を更新しません。  
  
 したがって、モデルに対する変更は次のようなテストで保護する必要があります。  
  
```  
if (!store.InUndoRedoOrRollback   
         && !store. InSerializationTransaction)  
{ this.TextLength = ...; // in-store changes   
}  
```  
  
 対照的に、プロパティ ハンドラーが、たとえばファイル、データベース、またはストア以外の変数など、ストアの外側に変更を伝達する場合、ユーザーが元に戻したり、やり直したりするときに、外部の値が更新されるように、それらの変更を常に実行する必要があります。  
  
### <a name="canceling-a-change"></a>変更の取り消し  
 変更を防ぐ場合、現在のトランザクションをロールバックできます。 たとえば、プロパティが常に特定の範囲内になるようにすることが望ましい場合があるかもしれません。  
  
```  
if (newValue > 10)   
{ store.TransactionManager.CurrentTransaction.Rollback();  
  System.Windows.Forms.MessageBox.Show("Value must be less than 10");  
}  
  
```  
  
### <a name="alternative-technique-calculated-properties"></a>代替手法: 計算されるプロパティ  
 前述の例は OnValueChanged() を使用して、あるドメイン プロパティから別のドメイン プロパティへ値を伝達する方法を示しています。 各プロパティは独自の格納値を持っています。  
  
 代わりに、派生したプロパティを Calculated property として定義することを検討できます。 その場合、プロパティは独自のストレージを持たず、値が必要になるときに常に関数が評価されることを定義しています。 詳細については、次を参照してください。[記憶域のカスタム プロパティして計算された](../modeling/calculated-and-custom-storage-properties.md)です。  
  
 設定することが、前の例ではなく、**種類**フィールド`TextLengthCount`する**計算**DSL 定義でします。 独自に提供するよう**取得**このドメインのプロパティのメソッドです。 **取得**メソッドは、現在の長さを返します、`Text`文字列。  
  
 ただし、計算されるプロパティの潜在的な欠点は、値が使用されるたびに式が評価されるため、パフォーマンスの問題が生じる可能性があることです。 また、計算されるプロパティに OnValueChanging() および OnValueChanged() はありません。  
  
### <a name="alternative-technique-change-rules"></a>代替手法: 変更規則  
 ChangeRule を定義する場合は、プロパティの値を変更するトランザクションの最後に実行されます。  詳細については、次を参照してください。[ルール反映されるまで変更内で、モデル](../modeling/rules-propagate-changes-within-the-model.md)です。  
  
 1 つのトランザクション内で複数の変更があった場合、ChangeRule はそれらすべてが完了したときに実行されます。 一方、... OnValue メソッドは、一部の変更が行われない場合に実行されます。 目的に応じて、ChangeRule が適切である場合があります。  
  
 また、特定の範囲内に保つために、プロパティの新しい値を調整するのに、ChangeRule を使用することができます。  
  
> [!WARNING]
>  ある規則がストア コンテンツに対して変更を加えた場合、他の規則とプロパティ ハンドラーがトリガーされることがあります。 規則がそれ自体をトリガーしたプロパティを変更した場合、その規則は再度呼び出されることになります。 終わりのないトリガーにならないように注意して規則を定義してください。  
  
```  
using Microsoft.VisualStudio.Modeling;   
...  
// Change rule on the domain class Comment:  
[RuleOn(typeof(Comment), FireTime = TimeToFire.TopLevelCommit)]   
class MyCommentTrimRule : ChangeRule  
{  
  public override void   
    ElementPropertyChanged(ElementPropertyChangedEventArgs e)  
  {  
    base.ElementPropertyChanged(e);  
    Comment comment = e.ModelElement as Comment;  
  
    if (comment.Text.StartsWith(" ") || comment.Text.EndsWith(" "))  
      comment.Text = comment.Text.Trim();  
    // If changed, rule will trigger again.  
  }  
}  
  
// Register the rule:   
public partial class MyDomainModel   
{  
 protected override Type[] GetCustomDomainModelTypes()   
 { return new Type[] { typeof(MyCommentTrimRule) };   
 }  
}  
  
```  
  
## <a name="example"></a>例  
  
### <a name="description"></a>説明  
 以下の例はドメイン プロパティのプロパティ ハンドラーをオーバーライドし、`ExampleElement` ドメイン クラスのプロパティが変更された場合、ユーザーに通知します。  
  
### <a name="code"></a>コード  
  
```  
using DslModeling = global::Microsoft.VisualStudio.Modeling;  
using DslDesign = global::Microsoft.VisualStudio.Modeling.Design;  
  
namespace msft.FieldChangeSample  
{  
  public partial class ExampleElement  
  {  
    internal sealed partial class NamePropertyHandler  
    {  
      protected override void OnValueChanged(ExampleElement element,  
         string oldValue, string newValue)  
      {  
        if (!this.Store.InUndoRedoOrRollback)  
        {  
           // make in-store changes here...  
        }  
        // This part is called even in undo:  
        System.Windows.Forms.MessageBox.Show("Value Has Changed");  
        base.OnValueChanged(element, oldValue, newValue);  
      }  
    }  
  }  
}  
```  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualStudio.Modeling.DomainPropertyValueHandler%602.OnValueChanged%2A>   
 <xref:Microsoft.VisualStudio.Modeling.DomainPropertyValueHandler%602.OnValueChanging%2A>