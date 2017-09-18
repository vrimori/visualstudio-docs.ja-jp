---
title: "Reorder Parameters Refactoring (C#) | Microsoft Docs"
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
  - "vs.csharp.refactoring.reorder"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "refactoring [C#], Reorder Parameters"
  - "Reorder Parameters refactoring [C#]"
ms.assetid: 4dabf21a-a9f0-41e9-b11b-55760cf2bd90
caps.latest.revision: 26
caps.handback.revision: 26
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Reorder Parameters Refactoring (C#)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

`Reorder Parameters` は、メソッド、インデクサー、およびデリゲートのパラメーターの順序を簡単に変更できる Visual C\# リファクタリング操作です。  `Reorder Parameters` によって宣言が変更され、メンバーが呼び出されるすべての場所で、パラメーターが新しい順序を反映するように再配置されます。  
  
 `Reorder Parameters` の操作を実行するには、メソッド、インデクサー、またはデリゲートの上か横にカーソルを移動します。  カーソルを移動したら、ショートカット キーを使用するか、またはショートカット メニューのコマンドをクリックして、`Reorder Parameters` を呼び出します。  
  
> [!NOTE]
>  拡張メソッドの最初のパラメーターの順序を変更することはできません。  
  
### パラメーターを並べ替えるには  
  
1.  `ReorderParameters` という名前のクラス ライブラリを作成し、`Class1` を次のプログラム例で置き換えます。  
  
    ```c#  
    class ProtoClassA  
    {  
        // Invoke on 'MethodB'.  
        public void MethodB(int i, bool b) { }  
    }  
  
    class ProtoClassC  
    {  
        void D()  
        {  
            ProtoClassA MyClassA = new ProtoClassA();  
  
            // Invoke on 'MethodB'.  
            MyClassA.MethodB(0, false);  
        }  
    }  
    ```  
  
2.  メソッド宣言またはメソッド呼び出しで、`MethodB` にカーソルを移動します。  
  
3.  **\[リファクター\]** メニューの **\[パラメーター順序の再変更\]** をクリックします。  
  
     **\[パラメーターの順番の再変更\]** ダイアログ ボックスが表示されます。  
  
4.  **\[パラメーター順序の再変更\]** ダイアログ ボックスの **\[パラメーター\]** ボックスで \[`int i`\] を選択し、ダウン ボタンをクリックします。  
  
     または、**\[パラメーター\]** ボックスで \[`bool b`\] の後の \[`int i`\] をドラッグする方法もあります。  
  
5.  **\[パラメーター順序の再変更\]** ダイアログ ボックスで、**\[OK\]** をクリックします。  
  
     **\[パラメーター順序の再変更\]** ダイアログ ボックスの **\[参照の変更のプレビュー\]** チェック ボックスがオンの場合は、**\[変更のプレビュー \- パラメーターの順番の再変更\]** ダイアログ ボックスが表示されます。  メソッド シグネチャとメソッド呼び出しの両方における `MethodB` のパラメーター リストの変更がプレビューされます。  
  
    1.  **\[変更のプレビュー \- パラメーターの順番の再変更\]** ダイアログ ボックスが表示された場合は、**\[適用\]** をクリックします。  
  
         この例では、`MethodB` のメソッド宣言とすべてのメソッド呼び出しサイトが更新されます。  
  
## 解説  
 メソッド宣言またはメソッド呼び出しからパラメーターの順序を変更できます。  カーソルはメソッドまたはデリゲートの宣言の上か横に移動し、コードの本体には移動しないでください。  
  
## 参照  
 [Refactoring \(C\#\)](../csharp-ide/refactoring-csharp.md)