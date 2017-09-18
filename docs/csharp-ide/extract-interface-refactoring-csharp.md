---
title: "Extract Interface Refactoring (C#) | Microsoft Docs"
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
  - "vs.csharp.refactoring.extractinterface"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "refactoring [C#], Extract Interface"
  - "Extract Interface refactoring operation [C#]"
ms.assetid: 7d0aa225-3b33-4331-9652-5a67cac6f3d0
caps.latest.revision: 25
caps.handback.revision: 25
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Extract Interface Refactoring (C#)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

\[インターフェイスの抽出\] は、既存のクラス、構造体、またはインターフェイスに基づくメンバーを使用して新規インターフェイスを簡単に作成できるリファクタリング操作です。  
  
 複数のクライアントで使用するクラス、構造体、またはインターフェイスのメンバーのサブセットが同じ場合、または複数のクラス、構造体、またはインターフェイスがメンバーのサブセットを共有する場合は、インターフェイスにメンバーのサブセットを組み入れることが便利なことがあります。  インターフェイスの使用の詳細については、「[インターフェイス](/dotnet/csharp/programming-guide/interfaces/index)」を参照してください。  
  
 \[インターフェイスの抽出\] では、新規ファイル内にインターフェイスが生成され、その新規ファイルの先頭にカーソルが移動します。  新規インターフェイスに対して抽出するメンバー、新規インターフェイスの名前、および生成されるファイルの名前は、**\[インターフェイスの抽出\]** ダイアログ ボックスを使用して指定できます。  
  
### \[インターフェイスの抽出\] を使用するには  
  
1.  `ExtractInterface` という名前のコンソール アプリケーションを作成し、`Program` を次のコードで置き換えます。  
  
    ```c#  
    // Invoke Extract Interface on ProtoA.  
    // Note:  the extracted interface will be created in a new file.  
    class ProtoA  
    {  
        public void MethodB(string s) { }  
    }  
    ```  
  
2.  カーソルを `MethodB` に移動し、**\[リファクター\]** メニューの **\[インターフェイスの抽出\]** をクリックします。  
  
     **\[インターフェイスの抽出\]** ダイアログ ボックスが表示されます。  
  
     キーボード ショートカットとして Ctrl キーを押しながら R キーを押し、次に I キーを押すことでも、**\[インターフェイスの抽出\]** ダイアログ ボックスを表示できます。  
  
     **\[インターフェイスの抽出\]** ダイアログ ボックスを表示するには、マウスを右クリックし、**\[リファクター\]** をポイントし、**\[インターフェイスの抽出\]** をクリックする方法もあります。  
  
3.  **\[すべて選択\]** をクリックします。  
  
4.  **\[OK\]** をクリックします。  
  
     新規ファイル IProtoA.cs と次のコードが表示されます。  
  
    ```c#  
    using System;  
    namespace TopThreeRefactorings  
    {  
        interface IProtoA  
        {  
            void MethodB(string s);  
        }  
    }  
    ```  
  
## 解説  
 この機能は、抽出するメンバーが含まれるクラス、構造体、またはインターフェイスにカーソルが位置しているときだけ利用できます。  カーソルがこの位置に置かれているときに、\[インターフェイスの抽出\] リファクタリング操作を呼び出してください。  
  
 クラスまたは構造体でインターフェイスの抽出を呼び出す場合、新規のインターフェイス名が含まれるように、ベースおよびインターフェイスの一覧が変更されます。  インターフェイスでインターフェイスの抽出を呼び出す場合、ベースおよびインターフェイスの一覧は変更されません。  
  
## 参照  
 [Refactoring \(C\#\)](../csharp-ide/refactoring-csharp.md)