---
title: メソッドの抽出リファクタリング (c#) |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.csharp.refactoring.extractmethod
dev_langs:
- CSharp
helpviewer_keywords:
- refactoring [C#], Extract Method
- Extract Method refactoring operation [C#]
ms.assetid: eeba11df-a815-4bec-9c21-8a831891b783
caps.latest.revision: 29
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 7aaa6570382fe296cc58f3d41d451250eafe6537
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47548328"
---
# <a name="extract-method-refactoring-c"></a>メソッドの抽出リファクタリング (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**メソッドの抽出**リファクタリング操作で既存のメンバーのコードから新しいメソッドを作成する簡単な方法を提供します。  
  
 使用して**メソッドの抽出**、選択した既存のメンバーのコード ブロック内からコードを抽出することで新しいメソッドを作成することができます。 新しい、抽出されたメソッドには、選択したコードが含まれていて、既存のメンバーで、選択したコードは新しいメソッドの呼び出しに置き換えられます。 独自のメソッドにコードのフラグメントを変換して、簡単にすることができます、正確に再利用と読みやすさの向上のためのコードを再構成します。  
  
 **メソッドの抽出**次の利点があります。  
  
-   再利用可能な個別のメソッドを目立たせることで、コーディングのベスト プラクティスをお勧めします。  
  
-   適切な組織でのコードを自己文書化を促進します。  
  
     わかりやすい名前が使用されている高度な方法の詳細は一連のコメントをなどことができます。  
  
-   メソッドをオーバーライドする簡略化に細かい単位の作成をお勧めします。  
  
-   コードの重複を削減します。  
  
### <a name="to-use-extract-method"></a>メソッドの抽出を使用するには  
  
1.  `ExtractMethod` という名前のコンソール アプリケーションを作成し、`Program` を次のコード例で置き換えます。  
  
    ```csharp  
    class A  
    {  
        const double PI = 3.141592;  
  
        double CalculatePaintNeeded(double paintPerUnit, double radius)  
        {  
            // Select any of the following:  
            // 1. The entire next line of code.  
            // 2. The right-hand side of the next line of code.  
            // 3. Just "PI *" of the right-hand side of the next line  
            //    of code (to see the prompt for selection expansion).  
            // 4.  All code within the method body.  
            // ...Then invoke Extract Method.  
  
            double area = PI * radius * radius;  
  
            return area / paintPerUnit;  
        }  
    }  
    ```  
  
2.  抽出するコード フラグメントを選択します。  
  
    ```csharp  
    double area = PI * radius * radius;  
    ```  
  
3.  **リファクタリング** メニューのをクリックして**メソッドの抽出**します。  
  
     **メソッドの抽出** ダイアログ ボックスが表示されます。  
  
     または、キーボード ショートカット CTRL + R を表示するには M 入力も、**メソッドの抽出** ダイアログ ボックス。  
  
     右、選択したコードをポイントして、**リファクタリング**、 をクリックし、**メソッドの抽出**を表示する、**メソッドの抽出** ダイアログ ボックス。  
  
4.  新規のメソッドの名前を指定します。`CircleArea`の、**新しいメソッドの名前**ボックス。  
  
     新しいメソッドのシグネチャのプレビューを表示します**メソッド シグネチャのプレビュー**します。  
  
5.  **[OK]** をクリックします。  
  
## <a name="remarks"></a>Remarks  
 使用すると、**メソッドの抽出**コマンドを次のソース メンバーを同じクラスの新しいメソッドを挿入します。  
  
## <a name="partial-types"></a>部分型  
 クラスが部分の型の場合**メソッドの抽出**ソース メンバーの直後に続く新しいメソッドが生成されます。 **メソッドの抽出**インスタンス データが新しいメソッドのコードで参照されていない場合は、静的メソッドを作成する、新しいメソッドのシグネチャを決定します。  
  
## <a name="generic-type-parameters"></a>ジェネリック型の型パラメーター  
 制約のないジェネリック型パラメーターを持つメソッドを抽出するときに生成されたコードは追加されません、`ref`修飾子パラメーターに値が割り当てられていない場合。 抽出されたメソッドがジェネリック型引数として参照型をサポートするかどうかは、手動で追加する必要があります、`ref`修飾子をメソッド シグネチャのパラメーター。  
  
## <a name="anonymous-methods"></a>匿名メソッド  
 宣言または匿名メソッドの外部から参照されているローカル変数への参照を含む匿名メソッドの一部を抽出しようとする場合、Visual Studio について警告する潜在的なセマンティクスの変更。  
  
 匿名メソッドは、ローカル変数の値を使用する場合、値は、匿名メソッドが実行される時点で取得されます。 別の方法に匿名メソッドの抽出時に、ローカル変数の値は、抽出されたメソッドの呼び出しの時点で取得されます。  
  
 次の例では、このセマンティクスの変更を示します。 このコードが実行される場合**11**コンソールに出力されます。 使用する場合**メソッドの抽出**を独自のメソッドにコード コメントでマークされているコードの領域を抽出し、リファクタリング後のコードを実行し、 **10**コンソールに出力されます。  
  
```csharp  
class Program  
{  
    delegate void D();  
    D d;  
    static void Main(string[] args)  
    {  
        Program p = new Program();  
        int i = 10;  
        /*begin extraction*/  
            p.d = delegate { Console.WriteLine(i++); };  
        /*end extraction*/  
        i++;  
        p.d();  
    }  
}  
```  
  
 このような状況を回避するには、クラスのフィールドの匿名メソッドで使用されるローカル変数を確認します。  
  
## <a name="see-also"></a>関連項目  
 [リファクタリング (C#)](../csharp-ide/refactoring-csharp.md)