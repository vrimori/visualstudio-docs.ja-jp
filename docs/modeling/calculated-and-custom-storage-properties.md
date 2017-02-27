---
title: "計算されると、カスタムの記憶域のプロパティ | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ドメインのプロパティをプログラミングのドメイン固有言語"
ms.assetid: 42b785f9-2b0f-4f13-a6b4-246e5e0d477a
caps.latest.revision: 19
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 19
---
# 計算されると、カスタムの記憶域のプロパティ
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

ドメイン固有言語 \(DSL\) 内のすべてのドメイン プロパティは、ダイアグラムでクリックし、言語エクスプ ローラーで、ユーザーに表示されることができ、プログラム コードからアクセスできます。 ただし、プロパティは、その値を格納するように異なります。  
  
## ドメイン プロパティの種類  
 DSL 定義で設定することができます、 **種類** の次の表に記載されているドメインのプロパティ。  
  
|ドメイン プロパティの種類|説明|  
|-------------------|--------|  
|**標準** \(既定\)|ドメイン プロパティに保存されている、 *格納* ファイルにシリアル化されたとします。|  
|**計算**|ストアでは保存されませんが、その他の値から計算される読み取り専用ドメイン プロパティ。<br /><br /> たとえば、 `Person.Age` から計算でした `Person.BirthDate`します。<br /><br /> 計算を実行するコードを指定する必要があります。 通常、その他のドメインのプロパティから値を計算します。 ただし、外部リソースを使用することもできます。|  
|**カスタム ストレージ**|ドメイン プロパティがない場合、ストアに直接保存されているが、get および設定できます。<br /><br /> 取得し、値を設定する方法を提供する必要があります。<br /><br /> たとえば、 `Person.FullAddress` に格納 `Person.StreetAddress`, 、`Person.City`, 、および `Person.PostalCode`です。<br /><br /> 取得し、データベースから値を設定する例については、外部のリソースをアクセスすることもできます。<br /><br /> コードでは、ストア内の値を設定する必要がありますと `Store.InUndoRedoOrRollback` は true です。 参照してください [トランザクションとカスタムの set アクセス操作子](#setters)します。|  
  
## 計算された、またはカスタムのストレージ プロパティのコードを提供します。  
 計算またはカスタム ストレージ ドメイン プロパティの種類を設定する場合は、アクセス方法を指定する必要です。 ソリューションをビルドするときにエラー レポートを教えてくれる何が必要です。  
  
#### 集計またはカスタム ストレージ\] プロパティを定義するには  
  
1.  DslDefinition.dsl での図に、または \[ドメイン プロパティを選択 **DSL エクスプ ローラー**します。  
  
2.  **プロパティ** ウィンドウで、設定、 **種類** フィールドを **Calculated** または **カスタム ストレージ**します。  
  
     設定されていることを確認、 **型** 目的にします。  
  
3.  クリックして **すべてのテンプレートの変換** のツールバーで **ソリューション エクスプ ローラー**します。  
  
4.  **\[ビルド\]** メニューの **\[ソリューションのビルド\]** をクリックします。  
  
     次のエラー メッセージが表示されます:"*YourClass* Get コマンドの定義が含まれていない*YourProperty*."  
  
5.  エラー メッセージをダブルクリックします。  
  
     Dsl\\GeneratedCode\\DomainClasses.cs または DomainRelationships.cs が開きます。 強調表示されているメソッド呼び出しの上コメント Get の実装を提供するよう求める*YourProperty*\(\)。  
  
    > [!NOTE]
    >  このファイルは、DslDefinition.dsl から生成されます。 このファイルを編集する場合、変更は失われます\] をクリックして、次回 **すべてのテンプレートの変換**します。 代わりに、別のファイルに必要なメソッドを追加します。  
  
6.  作成または別のフォルダー、たとえば CustomCode\\ で、クラス ファイルを開きます*YourDomainClass*. cs です。  
  
     名前空間が、生成されたコードのように同じであることを確認します。  
  
7.  クラス ファイルでは、ドメイン クラスの実装の一部を記述します。 クラスで、不足しているの定義を記述 `Get` メソッドを次の例のようになります。  
  
    ```  
    namespace Company.FamilyTree  
    {  public partial class Person  
       {  int GetAgeValue()  
          { return System.DateTime.Today.Year - this.BirthYear; }  
    }  }  
    ```  
  
8.  設定した場合 **種類** に **カスタム ストレージ**, 、提供する必要があります、 `Set` メソッドです。 例:  
  
    ```  
    void SetAgeValue(int value)  
    { if (!Store.InUndoRedoOrRollback)  
        this.BirthYear =   
            System.DateTime.Today.Year - value; }  
    ```  
  
     コードでは、ストア内の値を設定する必要がありますと `Store.InUndoRedoOrRollback` は true です。 参照してください [トランザクションとカスタムの set アクセス操作子](#setters)します。  
  
9. ソリューションをビルドして実行します。  
  
10. プロパティをテストします。 試してみることを確認 **を元に戻す** と **やり直し**します。  
  
##  <a name="setters"></a> トランザクションとカスタムの set アクセス操作子  
 カスタム ストレージ\] プロパティの Set メソッドでないを開くには、トランザクション メソッドは通常、アクティブなトランザクションの内部と呼ばれるためです。  
  
 ただし、Set メソッドは、ユーザーが元に戻したりやり直したりを呼び出す場合、またはトランザクションのロールバックにも呼び出すことがあります。<xref:Microsoft.VisualStudio.Modeling.Store.InUndoRedoOrRollback%2A> が true の場合、Set メソッドを次のように動作する必要があります。  
  
-   他のドメイン プロパティに値の割り当てなどのストアに変更はください必要があります。 アンドゥ マネージャーはその値を設定します。  
  
-   ただし、データベースまたはファイルの内容、または、ストア外のオブジェクトなど、任意の外部リソースを更新する必要があります。 これにより、それらに格納されている synchronism ストア内の値を持つことを確認します。  
  
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
  
 トランザクションの詳細については、次を参照してください。 [プログラム コードにおけるモデル内の移動およびモデルの更新](../modeling/navigating-and-updating-a-model-in-program-code.md)します。  
  
## 参照  
 [プログラム コードにおけるモデル内の移動およびモデルの更新](../modeling/navigating-and-updating-a-model-in-program-code.md)   
 [ドメイン プロパティのプロパティ](../modeling/properties-of-domain-properties.md)   
 [方法: ドメイン固有言語を定義する](../modeling/how-to-define-a-domain-specific-language.md)