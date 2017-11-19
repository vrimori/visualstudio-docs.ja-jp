---
redirect_url: /visualstudio/csharp-ide/refactoring/change-method-signature
title: "パラメーターの削除リファクタリング (c#) |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.csharp.refactoring.remove
dev_langs: CSharp
helpviewer_keywords:
- parameters [C#], removing
- refactoring [C#], Remove Parameters
- Remove Parameters refactoring [C#]
ms.assetid: f4fc3265-0ef8-4398-a691-c338178697a6
caps.latest.revision: "24"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d5e53d813d9b2dcefd2b2d19da2a76b6c0d1f989
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="remove-parameters-refactoring-c"></a>パラメーターの削除リファクタリング (C#)
`Remove Parameters`メソッド、インデクサー、またはデリゲートからパラメーターを削除する簡単な方法を提供するリファクタリング操作です。 パラメーターの変更; 宣言を削除します。メンバーが呼び出されているすべての場所では、新規の宣言を反映するように、パラメーターが削除されます。  
  
 パラメーターの削除操作を実行するには、最初にメソッド、インデクサー、またはデリゲートでカーソルを配置します。 削除を呼び出すための位置にカーソルが中に`Parameters`操作、 をクリックして、**リファクター**  メニューの は、キーボード ショートカット キーを押すか、ショートカット メニューからコマンドを選択します。  
  
> [!NOTE]
>  拡張メソッドの最初のパラメーターを削除することはできません。  
  
### <a name="to-remove-parameters"></a>パラメーターを削除する  
  
1.  というコンソール アプリケーションを作成`RemoveParameters`、し、置き換えます`Program`を次のコード。  
  
    ```csharp  
    class A  
    {  
        // Invoke on 'A'.  
        public A(string s, int i) { }  
    }  
  
    class B  
    {  
        void C()  
        {  
            // Invoke on 'A'.  
            A a = new A("a", 2);  
        }  
    }  
    ```  
  
2.  メソッドにカーソルを置き`A`メソッドの宣言またはメソッドの呼び出しのいずれか。  
  
3.  **リファクター**メニューの [**パラメーターの削除**を表示する、**パラメーターの削除**] ダイアログ ボックス。  
  
     キーボード ショートカット CTRL + R、V を表示するのにを入力することも、**パラメーターの削除** ダイアログ ボックス。  
  
     カーソルを右クリックすることもできますをポイント**リファクター**、順にクリック**パラメーターの削除**を表示する、**パラメーターの削除** ダイアログ ボックス。  
  
4.  使用して、**パラメーター**フィールドにカーソルを置き、 `int i`、クリックして**削除**です。  
  
5.  **[OK]** をクリックします。  
  
6.  **変更のプレビュー: パラメーターの削除**ダイアログ ボックスで、をクリックして**適用**です。  
  
## <a name="remarks"></a>コメント  
 メソッドの宣言またはメソッドの呼び出しからパラメーターを削除することができます。 メソッドの宣言またはデリゲートの名前のカーソルを配置し、パラメーターの削除を呼び出します。  
  
> [!CAUTION]
>  メソッドの本体でそのパラメーターへの参照は削除されませんが、メンバーの本体で参照されているパラメーターを削除するパラメーターを有効を削除します。 ビルド エラーが発生するコードにこのことができます。 ただし、使用することができます、**変更のプレビュー**リファクタリング操作を実行する前に、コードの確認 ダイアログ ボックス。  
  
 メソッドへの呼び出し中に削除されるパラメーターを変更する場合、パラメーターの削除、変更も削除されます。 たとえば、メソッドを呼び出す場合はからを変更します。  
  
```csharp  
MyMethod(param1++, param2);  
```  
  
 から  
  
```csharp  
MyMethod(param2);  
```  
  
 リファクタリングの操作によって`param1`は増加しません。  
  
## <a name="see-also"></a>関連項目  
 [リファクタリング (C#)](refactoring-csharp.md)