---
redirect_url: /visualstudio/csharp-ide/refactoring/change-method-signature
title: "リファクタリング (c#) パラメーターを並べ替える |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.csharp.refactoring.reorder
dev_langs: CSharp
helpviewer_keywords:
- refactoring [C#], Reorder Parameters
- Reorder Parameters refactoring [C#]
ms.assetid: 4dabf21a-a9f0-41e9-b11b-55760cf2bd90
caps.latest.revision: "26"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: 3a011794599bf1e56e905a40c6269b5639abadb2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="reorder-parameters-refactoring-c"></a>パラメーター順序の再変更リファクタリング (C#)
`Reorder Parameters`Visual c# リファクタリング操作メソッド、インデクサー、およびデリゲートのパラメーターの順序を変更する簡単な方法です。 `Reorder Parameters`宣言を変更し、任意の場所は、メンバーが呼び出された場合、パラメーターが新しい順序を反映するように再配置します。  
  
 実行する、`Reorder Parameters`またはメソッド、インデクサー、またはデリゲートの横にある操作にカーソルを置きます。 カーソルの位置がある場合を呼び出して、`Reorder Parameters`操作をショートカット キーを押すか、ショートカット メニューからコマンドをクリックします。  
  
> [!NOTE]
>  拡張メソッドの最初のパラメーターの順序を変更することはできません。  
  
### <a name="to-reorder-parameters"></a>パラメーターの順序を変更するには  
  
1.  という名前のクラス ライブラリを作成する`ReorderParameters`、し、置き換えます`Class1`次のコード例を使用します。  
  
    ```csharp  
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
  
2.  カーソルを置き`MethodB`メソッドの宣言またはメソッドの呼び出しのいずれか。  
  
3.  **リファクター**  メニューのをクリックして**パラメーターの順序を変更**です。  
  
     **パラメーターの順序を変更** ダイアログ ボックスが表示されます。  
  
4.  **パラメーターの順序を変更**ダイアログ ボックスで、`int i`で、**パラメーター**一覧、および下矢印ボタンをクリックします。  
  
     ドラッグする代わりに、`int i`後`bool b`で、**パラメーター**  ボックスの一覧です。  
  
5.  **パラメーターの順序を変更**ダイアログ ボックスで、をクリックして**OK**です。  
  
     場合、**参照の変更のプレビュー**オプションがオン、**パラメーターの順序を変更** ダイアログ ボックスで、**変更のプレビューのパラメーターの順序を変更** ダイアログ ボックスが表示されます。 パラメーター リストの変更のプレビュー提供`MethodB`シグネチャとメソッドの呼び出しの両方でします。  
  
    1.  場合、**プレビューの変更 - [パラメーター順序**] ダイアログ ボックスが表示されたら、をクリックして**適用**です。  
  
         この例では、メソッドの宣言とすべてのメソッド呼び出しのサイト`MethodB`更新されます。  
  
## <a name="remarks"></a>コメント  
 メソッドの宣言またはメソッドの呼び出しからのパラメーターの順序を変更することができます。 メソッドまたはデリゲートの宣言の横にある、または本文ではなくでカーソルを置きます。  
  
## <a name="see-also"></a>参照  
 [リファクタリング (C#)](refactoring-csharp.md)