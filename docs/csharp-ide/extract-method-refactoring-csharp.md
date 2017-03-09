---
title: "メソッドの抽出リファクタリング (C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.csharp.refactoring.extractmethod"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "リファクタリング [C#], メソッドの抽出"
  - "[メソッドの展開] リファクタリング操作 [C#]"
ms.assetid: eeba11df-a815-4bec-9c21-8a831891b783
caps.latest.revision: 29
caps.handback.revision: 29
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# メソッドの抽出リファクタリング (C#)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

**\[メソッドの抽出\]** は、既存のメンバーのコード片から新規メソッドを簡単に作成できるリファクタリング操作です。  
  
 **\[メソッドの抽出\]** を使用すると、既存メンバーのコード ブロック内からコードの選択部分を抽出することで、新規メソッドを作成できます。  抽出された新しいメソッドには選択したコードが含められ、既存のメンバー内の選択したコードは、新規メソッドへの呼び出しに置き換えられます。  コード片を独立したメソッドにすることで、コードをすばやく正確に再構成でき、再利用性と読みやすさが向上します。  
  
 **\[メソッドの抽出\]** には、次の利点があります。  
  
-   メソッドの独立性と再利用可能性を重視することで、コーディングの推奨手順を遵守できる。  
  
-   適切に構成することで、コードを自己文書化できる。  
  
     説明的な名前を使用すると、高水準のメソッドも一連のコメントのように読みやすくなる。  
  
-   オーバーライドを単純にするために、詳細なメソッドの作成が促進される。  
  
-   コードの重複を減らすことができる。  
  
### \[メソッドの展開\] を使用するには  
  
1.  `ExtractMethod` という名前のコンソール アプリケーションを作成し、`Program` を次のプログラム例で置き換えます。  
  
    ```c#  
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
  
2.  抽出するコード片を選択します。  
  
    ```c#  
    double area = PI * radius * radius;  
  
    ```  
  
3.  **\[リファクター\]** メニューの **\[メソッドの展開\]** をクリックします。  
  
     **\[メソッドの抽出\]** ダイアログ ボックスが表示されます。  
  
     または、キーボード ショートカットとして Ctrl キーを押しながら R キーを押し、次に M キーを押すことでも、**\[メソッドの展開\]** ダイアログ ボックスを表示できます。  
  
     **\[メソッドの展開\]** ダイアログ ボックスを表示するには、選択したコードを右クリックし、**\[リファクター\]** をポイントし、**\[メソッドの展開\]** をクリックする方法もあります。  
  
4.  **\[新しいメソッド名\]** ボックスに新規メソッドの名前 \(たとえば「`CircleArea`」\) を入力します。  
  
     新規メソッド シグネチャのプレビューが **\[メソッド シグネチャのプレビュー\]** に表示されます。  
  
5.  **\[OK\]** をクリックします。  
  
## 解説  
 **\[メソッドの抽出\]** を使用すると、新規メソッドが同じクラスのソース メンバーの後に挿入されます。  
  
## 部分型  
 クラスが部分型である場合は、**\[メソッドの抽出\]** によって新規メソッドがソース メンバーの直後に作成されます。  **\[メソッドの抽出\]** では、新規メソッドのシグネチャを決定し、新規メソッド内のコードでインスタンス データが参照されていない場合は静的メソッドを作成します。  
  
## ジェネリック型パラメーター  
 制約のないジェネリック型パラメーターを持つメソッドを抽出する場合、生成されるコードでは、そのパラメーターに値が割り当てられない限り `ref` 修飾子は追加されません。  抽出されたメソッドでジェネリック型引数として参照型をサポートする場合は、メソッド シグネチャ内のパラメーターに手動で `ref` 修飾子を追加する必要があります。  
  
## 匿名メソッド  
 匿名メソッドにローカル変数への参照が含まれていて、そのローカル変数が匿名メソッドの外部で宣言または参照されている場合、匿名メソッドの一部を抽出しようとすると、セマンティクスが変更される可能性があるという警告が表示されます。  
  
 匿名メソッドでローカル変数の値を使用する場合、その値は匿名メソッドの実行時に取得されます。  匿名メソッドが別のメソッドに抽出される場合、ローカル変数の値は、抽出されたメソッドの呼び出し時に取得されます。  
  
 このセマンティクスの変更について、次に例を示します。  このコードを実行すると、コンソールには "**11**" が出力されます。  **\[メソッドの抽出\]** を使用して、コード コメントでマークされているコードの一部を独自メソッドに抽出し、その後リファクタリングされたコードを実行すると、コンソールには "**10**" が出力されます。  
  
```c#  
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
  
 この問題を回避するには、匿名メソッドで使用されているローカル変数をクラスのフィールドにします。  
  
## 参照  
 [Refactoring \(C\#\)](../csharp-ide/refactoring-csharp.md)