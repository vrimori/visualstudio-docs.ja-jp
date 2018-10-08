---
title: パラメーターの削除リファクタリング (c#) |Microsoft Docs
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
- vs.csharp.refactoring.remove
dev_langs:
- CSharp
helpviewer_keywords:
- parameters [C#], removing
- refactoring [C#], Remove Parameters
- Remove Parameters refactoring [C#]
ms.assetid: f4fc3265-0ef8-4398-a691-c338178697a6
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 529950d72ac11ebfd443a85db597adfcbc89bba1
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47546066"
---
# <a name="remove-parameters-refactoring-c"></a>パラメーターの削除リファクタリング (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`Remove Parameters` メソッド、インデクサー、またはデリゲートからパラメーターを削除する簡単な方法は、リファクタリング操作です。 パラメーターの変更; 宣言を削除します。メンバーが呼び出された場合のあらゆる場所に新しい宣言を反映するように、パラメーターが削除されます。  
  
 パラメーターの削除操作を実行するには、最初に、メソッド、インデクサー、またはデリゲートにカーソルを配置します。 呼び出す、削除の位置にカーソルがあるときに`Parameters`操作、 をクリックして、**リファクタリング** メニューの キーを押すキーボード ショートカット、または、ショートカット メニューからコマンドを選択します。  
  
> [!NOTE]
>  拡張メソッドの最初のパラメーターを削除することはできません。  
  
### <a name="to-remove-parameters"></a>パラメーターを削除する  
  
1.  という名前のコンソール アプリケーションを作成する`RemoveParameters`、し、置き換えます`Program`を次のコード。  
  
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
  
2.  メソッドにカーソルを置き`A`メソッドの宣言またはメソッドの呼び出しで。  
  
3.  **リファクタリング**メニューの [**パラメーターの削除**を表示する、**パラメーターの削除**] ダイアログ ボックス。  
  
     V を表示するのにはキーボード ショートカット CTRL + R を入力することも、**パラメーターの削除** ダイアログ ボックス。  
  
     カーソルを右クリックして をポイント**リファクタリング**、順にクリックします**パラメーターの削除**を表示する、**パラメーターの削除** ダイアログ ボックス。  
  
4.  使用して、**パラメーター**フィールドにカーソルを置き、 `int i`、 をクリックし、**削除**します。  
  
5.  **[OK]** をクリックします。  
  
6.  **変更のプレビュー-パラメーターの削除**ダイアログ ボックスで、をクリックして**適用**します。  
  
## <a name="remarks"></a>Remarks  
 メソッドの宣言またはメソッドの呼び出しからパラメーターを削除することができます。 メソッドの宣言またはデリゲートの名前にカーソルを配置し、パラメーターの削除を呼び出します。  
  
> [!CAUTION]
>  メソッドの本体でそのパラメーターに参照は削除されませんが、メンバーの本文で参照されているパラメーターを削除するパラメーターの有効を削除します。 コードにビルド エラーが生じる。 ただし、使用することができます、**変更のプレビュー**リファクタリング操作を実行する前に、コードを確認するダイアログ ボックス。  
  
 メソッドへの呼び出し中に削除するパラメーターが変更された場合、パラメーターの削除、変更も削除されます。 メソッドを呼び出す場合は変更など  
  
```csharp  
MyMethod(param1++, param2);  
```  
  
 から  
  
```csharp  
MyMethod(param2);  
```  
  
 リファクタリングの操作によって`param1`は増えません。  
  
## <a name="see-also"></a>関連項目  
 [リファクタリング (C#)](../csharp-ide/refactoring-csharp.md)