---
title: "計算およびカスタムのストレージ プロパティ |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Domain-Specific Language, programming domain properties
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 3d8749e87a25cc9243cf7e76a99b027975673ab4
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/13/2018
---
# <a name="calculated-and-custom-storage-properties"></a>計算プロパティおよびカスタム格納プロパティ
ドメイン固有言語 (DSL) ですべてのドメインのプロパティは、ダイアグラムでし、言語エクスプ ローラーで、ユーザーに表示することができ、プログラム コードによってアクセスできます。 ただし、プロパティは、その値が格納されるように異なります。  
  
## <a name="kinds-of-domain-properties"></a>ドメインのプロパティの種類  
 DSL 定義で設定することができます、**種類**ドメイン プロパティには、次の表に記載されているの。  
  
|ドメイン プロパティの種類|説明|  
|--------------------------|-----------------|  
|**標準**(既定)|ドメイン プロパティに保存されている、*格納*ファイルにシリアル化されたとします。|  
|**計算**|読み取り専用ドメイン プロパティは、ストアに保存されませんが、その他の値から計算されます。<br /><br /> たとえば、`Person.Age`から計算でした`Person.BirthDate`です。<br /><br /> 計算を実行するコードを指定する必要があります。 通常、その他のドメインのプロパティから値を計算します。 ただし、外部リソースを使用することもできます。|  
|**カスタム ストレージ**|ドメイン プロパティは、ストアに直接保存されませんが、get および set の両方を指定できます。<br /><br /> 取得し、値を設定する方法を提供する必要があります。<br /><br /> たとえば、`Person.FullAddress`に格納`Person.StreetAddress`、 `Person.City`、および`Person.PostalCode`です。<br /><br /> 取得し、データベースから値を設定する例については、外部のリソースをアクセスすることもできます。<br /><br /> コードでは、ストアに値を設定しないでくださいとき`Store.InUndoRedoOrRollback`は true です。 参照してください[トランザクションとカスタム Setter](#setters)です。|  
  
## <a name="providing-the-code-for-a-calculated-or-custom-storage-property"></a>計算された、またはカスタムのストレージ プロパティのコードを提供します。  
 集計またはカスタムの記憶域をドメイン プロパティの種類を設定した場合は、アクセス方法を指定する必要があります。 ソリューションをビルドするときにエラー レポートがわかります何が必要です。  
  
#### <a name="to-define-a-calculated-or-custom-storage-property"></a>計算やカスタム ストレージ プロパティを定義するには  
  
1.  DslDefinition.dsl でドメイン プロパティの図に、または 選択**DSL のエクスプ ローラー**です。  
  
2.  **プロパティ**ウィンドウで、設定、**種類**フィールドを**Calculated**または**カスタム ストレージ**です。  
  
     設定されていることを確認、**型**の対象となります。  
  
3.  をクリックして**すべてのテンプレートの変換**のツールバーに**ソリューション エクスプ ローラー**です。  
  
4.  **[ビルド]** メニューの **[ソリューションのビルド]**をクリックします。  
  
     次のエラー メッセージが表示されます:"*YourClass* Get の定義が含まれていません*YourProperty*"。  
  
5.  エラー メッセージをダブルクリックします。  
  
     Dsl\GeneratedCode\DomainClasses.cs または DomainRelationships.cs が開きます。 強調表示されているメソッドを呼び出す上コメント Get の実装を指定するように求め*YourProperty*()。  
  
    > [!NOTE]
    >  このファイルは、DslDefinition.dsl から生成されます。 このファイルを編集する場合、変更は失われます をクリックして、次回**すべてのテンプレートの変換**です。 代わりに、別のファイルに必要なメソッドを追加します。  
  
6.  作成したり、別のフォルダー、たとえば CustomCode クラス ファイルを開く\\*YourDomainClass*。 cs です。  
  
     名前空間が生成されたコードのものと同じであることを確認してください。  
  
7.  クラス ファイルでは、ドメイン クラスの実装の一部を記述します。 クラスでは、欠落しているの定義を書き込む`Get`メソッドを次の例のようになります。  
  
    ```  
    namespace Company.FamilyTree  
    {  public partial class Person  
       {  int GetAgeValue()  
          { return System.DateTime.Today.Year - this.BirthYear; }  
    }  }  
    ```  
  
8.  設定した場合**種類**に**カスタム ストレージ**、提供する必要があります、`Set`メソッドです。 例:  
  
    ```  
    void SetAgeValue(int value)  
    { if (!Store.InUndoRedoOrRollback)  
        this.BirthYear =   
            System.DateTime.Today.Year - value; }  
    ```  
  
     コードでは、ストアに値を設定しないでくださいとき`Store.InUndoRedoOrRollback`は true です。 参照してください[トランザクションとカスタム Setter](#setters)です。  
  
9. ソリューションをビルドして実行します。  
  
10. プロパティをテストします。 試してみることを確認してください**を元に戻す**と**やり直し**です。  
  
##  <a name="setters"></a>トランザクションとカスタムの Setter  
 カスタム ストレージ プロパティの Set メソッドにするため必要はありませんを開くには、トランザクション、メソッドは通常、アクティブなトランザクションの内部と呼ばれます。  
  
 ただし、Set メソッドは、ユーザーが元に戻したり、やり直したりを呼び出した場合、またはトランザクションがロールバックされている場合にも呼び出す可能性があります。 ときに<xref:Microsoft.VisualStudio.Modeling.Store.InUndoRedoOrRollback%2A>が true の場合、Set メソッドに次のように動作する必要があります。  
  
-   変更しないようになどその他のドメインのプロパティに値を割り当てる、ストアにします。 アンドゥ マネージャーはその値を設定します。  
  
-   ただし、これデータベースまたはファイルの内容、または外部のストア オブジェクトなど、任意の外部リソースに更新する必要があります。 これにより、それらに格納されている synchronism ストアに値を持つことを確認します。  
  
 例:  
  
```  
void SetAgeValue(int value)  
{   
  // If we are in Undo, no changes to Store objects:  
  if (!this.Store.InUndoRedoOrRollback)  
  {   
    this.BirthYear = System.DateTime.Today.Year - value;   
  }  
  // But always update external objects:  
  System.IO.File.WriteAllText(AgeFile, value);  
}  
```  
  
 トランザクションの詳細については、次を参照してください。[を移動すると、プログラム コードでモデルを更新する](../modeling/navigating-and-updating-a-model-in-program-code.md)です。  
  
## <a name="see-also"></a>参照  
 [移動して、プログラム コードでモデルを更新します。](../modeling/navigating-and-updating-a-model-in-program-code.md)   
 [ドメインのプロパティのプロパティ](../modeling/properties-of-domain-properties.md)   
 [方法: ドメイン固有言語を定義する](../modeling/how-to-define-a-domain-specific-language.md)