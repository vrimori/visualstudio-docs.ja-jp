---
title: 計算およびカスタム格納プロパティ |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, programming domain properties
ms.assetid: 42b785f9-2b0f-4f13-a6b4-246e5e0d477a
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: c1203b962627071d757dc1876a534977c574a813
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49179492"
---
# <a name="calculated-and-custom-storage-properties"></a>計算プロパティおよびカスタム格納プロパティ
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ドメイン固有言語 (DSL) 内のすべてのドメイン プロパティは、図では、言語エクスプ ローラーで、ユーザーに表示されることができ、プログラム コードからアクセスできます。 ただし、プロパティは、その値が格納される方法では異なります。  
  
## <a name="kinds-of-domain-properties"></a>ドメインのプロパティの種類  
 DSL 定義で設定することができます、**種類**の次の表に記載されているドメインのプロパティ。  
  
|ドメイン プロパティの種類|説明|  
|--------------------------|-----------------|  
|**標準**(既定)|ドメイン プロパティに保存されている、*格納*ファイルにシリアル化されたとします。|  
|**計算**|読み取り専用ドメイン プロパティは、ストアに保存されませんが、その他の値から計算です。<br /><br /> たとえば、`Person.Age`から計算でした`Person.BirthDate`します。<br /><br /> 計算を実行するコードを指定する必要があります。 通常、他のドメイン プロパティから値を計算します。 ただし、外部リソースを使用することもできます。|  
|**カスタム ストレージ**|ドメイン プロパティは、ストアに直接保存されませんが、get と set の両方にすることができますです。<br /><br /> 取得し、値を設定する方法を指定する必要があります。<br /><br /> たとえば、`Person.FullAddress`に格納される`Person.StreetAddress`、 `Person.City`、および`Person.PostalCode`します。<br /><br /> 取得し、データベースから値を設定する例については、外部のリソースにアクセスすることもできます。<br /><br /> コードでは、ストアに値を設定しないでくださいと`Store.InUndoRedoOrRollback`は true。 参照してください[トランザクションとカスタム セッター](#setters)します。|  
  
## <a name="providing-the-code-for-a-calculated-or-custom-storage-property"></a>計算された、またはカスタムのストレージ プロパティのコードを提供します。  
 計算またはカスタム ストレージ ドメイン プロパティの種類を設定する場合は、アクセス方法を指定する必要です。 ソリューションをビルドすると、エラー レポートは通知して何が必要です。  
  
#### <a name="to-define-a-calculated-or-custom-storage-property"></a>計算またはカスタム ストレージ プロパティを定義するには  
  
1.  DslDefinition.dsl、ダイアグラムで、またはでは、ドメイン プロパティを選択します。 **DSL エクスプ ローラー**します。  
  
2.  **プロパティ**ウィンドウで、設定、**種類**フィールドを**Calculated**または**カスタム ストレージ**します。  
  
     設定されていることを確認、**型**の対象となります。  
  
3.  クリックして**すべてのテンプレートの変換**のツールバーで**ソリューション エクスプ ローラー**します。  
  
4.  **[ビルド]** メニューの **[ソリューションのビルド]** をクリックします。  
  
     次のエラー メッセージを受信する:"*YourClass* Get の定義が含まれていない*YourProperty*"。  
  
5.  エラー メッセージをダブルクリックします。  
  
     Dsl\GeneratedCode\DomainClasses.cs または DomainRelationships.cs が開きます。 強調表示されているメソッドの呼び出しを上記コメント Get の実装を指定するように求め*YourProperty*()。  
  
    > [!NOTE]
    >  このファイルは、DslDefinition.dsl から生成されます。 このファイルを編集する場合、変更は失われます をクリックした次回**すべてのテンプレートの変換**します。 代わりに、別のファイルに必要なメソッドを追加します。  
  
6.  作成またはクラス ファイルを別のフォルダー、たとえば CustomCode に\\*YourDomainClass*。 cs します。  
  
     名前空間が、生成されたコードのように同じであることを確認します。  
  
7.  クラス ファイルでは、ドメイン クラスの実装の一部を記述します。 クラスで、不足しているの定義を記述`Get`次の例のようなメソッド。  
  
    ```  
    namespace Company.FamilyTree  
    {  public partial class Person  
       {  int GetAgeValue()  
          { return System.DateTime.Today.Year - this.BirthYear; }  
    }  }  
    ```  
  
8.  設定した場合**種類**に**カスタム ストレージ**、提供する必要がありますも、`Set`メソッド。 例えば:  
  
    ```  
    void SetAgeValue(int value)  
    { if (!Store.InUndoRedoOrRollback)  
        this.BirthYear =   
            System.DateTime.Today.Year - value; }  
    ```  
  
     コードでは、ストアに値を設定しないでくださいと`Store.InUndoRedoOrRollback`は true。 参照してください[トランザクションとカスタム セッター](#setters)します。  
  
9. ソリューションをビルドして実行します。  
  
10. プロパティをテストします。 試してみることを確認**を元に戻す**と**やり直し**します。  
  
##  <a name="setters"></a> トランザクションとカスタムの set アクセス操作子  
 カスタム ストレージ プロパティのセット メソッドで必要はありません、トランザクションを開始するメソッドは通常、アクティブなトランザクション内で呼び出されるためです。  
  
 ただし、Set メソッドは、Undo または Redo では、ユーザーが呼び出される場合、またはトランザクションがロールバックされている場合にも呼び出す可能性があります。 ときに<xref:Microsoft.VisualStudio.Modeling.Store.InUndoRedoOrRollback%2A>が true の場合、Set メソッドに次のように動作する必要があります。  
  
-   その他のドメイン プロパティに値を割り当てるなど、ストアで変更されることにする必要があります。 元に戻すマネージャーはその値を設定します。  
  
-   ただし、データベースまたはファイルの内容、または、ストア外のオブジェクトなど、任意の外部リソースを更新にする必要があります。 これにより、ストア内の値を持つ synchronism で維持されることを確認します。  
  
 例えば:  
  
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
  
 トランザクションの詳細については、次を参照してください。[を移動すると、プログラム コードでのモデルを更新する](../modeling/navigating-and-updating-a-model-in-program-code.md)します。  
  
## <a name="see-also"></a>関連項目  
 [移動して、プログラム コードでモデルを更新しています](../modeling/navigating-and-updating-a-model-in-program-code.md)   
 [ドメインのプロパティのプロパティ](../modeling/properties-of-domain-properties.md)   
 [方法: ドメイン固有言語を定義する](../modeling/how-to-define-a-domain-specific-language.md)



