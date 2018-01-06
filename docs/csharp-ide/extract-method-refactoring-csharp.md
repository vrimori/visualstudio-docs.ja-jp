---
redirect_url: /visualstudio/csharp-ide/refactoring/extract-method
title: "メソッドの抽出リファクタリング (c#) |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: CSharp
helpviewer_keywords:
- refactoring [C#], Extract Method
- Extract Method refactoring operation [C#]
ms.assetid: eeba11df-a815-4bec-9c21-8a831891b783
caps.latest.revision: "29"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: 18fc4c20b39341f884fb23b51822ce7f6e427007
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="extract-method-refactoring-c"></a>メソッドの抽出リファクタリング (C#)
**メソッドの抽出**既存のメンバーのコードから新しいメソッドを作成する簡単な方法を提供する移動スキーマ リファクタリング操作は、します。  
  
 使用して**メソッドの抽出**、選択した既存のメンバーのコード ブロック内からコードを抽出することで新しいメソッドを作成することができます。 抽出された、新しいメソッドには、選択されたコードが含まれているし、既存のメンバーで選択されているコードは、新しいメソッドの呼び出しに置き換えられます。 独自のメソッドのコード フラグメントに変える、簡単にすることができ、正確に再利用して読みやすさの向上のためのコードを再構成します。  
  
 **メソッドの抽出**次の利点があります。  
  
-   Discrete、再利用可能なメソッドを強調することで、コーディングの推奨手順をお勧めします。  
  
-   適切に構成を使用してコードを自己文書化ことをお勧めします。  
  
     わかりやすい名前が使用されている高度なメソッドできます詳細などの一連のコメント。  
  
-   細かい単位のメソッドをオーバーライドする簡略化の作成を推奨します。  
  
-   コードの重複が減少します。  
  
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
  
3.  **リファクター**  メニューのをクリックして**メソッドの抽出**です。  
  
     **メソッドの抽出** ダイアログ ボックスが表示されます。  
  
     または、キーボード ショートカット CTRL + R、M を表示する入力も、**メソッドの抽出** ダイアログ ボックス。  
  
     ことができますもを右クリックし、選択したコードは、順にポイント**リファクター**、クリックして**メソッドの抽出**を表示する、**メソッドの抽出** ダイアログ ボックス。  
  
4.  など、新しいメソッドの名前を指定`CircleArea`で、**メソッド名を新しい**ボックス。  
  
     新しいメソッドのシグネチャのプレビューが表示されます。**メソッド シグネチャのプレビュー**です。  
  
5.  **[OK]**をクリックします。  
  
## <a name="remarks"></a>コメント  
 使用すると、**メソッドの抽出**コマンドを次のソース メンバーを同じクラスの新しいメソッドを挿入します。  
  
## <a name="partial-types"></a>部分型  
 クラスが部分型の場合は、に設定されている場合**メソッドの抽出**ソース メンバーのすぐ後、新しいメソッドが生成されます。 **メソッドの抽出**インスタンス データが新しいメソッドのコードで参照されていない場合は、静的メソッドを作成する、新しいメソッドのシグネチャを決定します。  
  
## <a name="generic-type-parameters"></a>ジェネリック型の型パラメーター  
 制約のないジェネリック型パラメーターを持つメソッドを抽出するときに生成されたコードは追加されません、`ref`修飾子をそのパラメーターに値が割り当てられていない限りです。 抽出されたメソッドがジェネリック型引数として参照型をサポートするかどうかは、手動で追加する必要があります、`ref`修飾子をメソッド シグネチャのパラメーターです。  
  
## <a name="anonymous-methods"></a>匿名メソッド  
 宣言または匿名メソッドの外部から参照されているローカル変数への参照を含む匿名メソッドの一部を抽出しようとする場合、Visual Studio について警告する潜在的なセマンティクスの変更。  
  
 匿名メソッドは、ローカル変数の値を使用する場合、値は、匿名メソッドが実行された時点で取得します。 別の方法に匿名メソッドの抽出時にローカル変数の値は、抽出されたメソッドの呼び出しの時点で取得されます。  
  
 次の例では、このセマンティクスの変更を示します。 このコードを実行する場合、 **11**は、コンソールに出力されます。 使用する場合**メソッドの抽出**を独自のメソッドにコード コメントでマークされているコードの領域を抽出し、リファクタリングされたコードの実行、 **10**は、コンソールに出力されます。  
  
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
  
## <a name="see-also"></a>参照  
 [リファクタリング (C#)](refactoring-csharp.md)