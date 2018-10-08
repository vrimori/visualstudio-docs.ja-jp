---
title: リファクタリング (c#) パラメーターを並べ替える |Microsoft Docs
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
- vs.csharp.refactoring.reorder
dev_langs:
- CSharp
helpviewer_keywords:
- refactoring [C#], Reorder Parameters
- Reorder Parameters refactoring [C#]
ms.assetid: 4dabf21a-a9f0-41e9-b11b-55760cf2bd90
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: d0d0428449ce5c78ae098a68d0466262cedd32ef
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47536777"
---
# <a name="reorder-parameters-refactoring-c"></a>パラメーター順序の再変更リファクタリング (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`Reorder Parameters` Visual c# リファクタリング操作メソッド、インデクサー、およびデリゲートのパラメーターの順序を変更する簡単な方法です。 `Reorder Parameters` 宣言を変更し、メンバーが呼び出された場合のあらゆる場所には、パラメーターが新しい注文を反映するように再配置。  
  
 実行する、`Reorder Parameters`またはメソッド、インデクサー、またはデリゲートの横にある操作にカーソルを置きます。 カーソルの位置があるときに呼び出す、`Reorder Parameters`キーを押して、キーボード ショートカット、または、ショートカット メニューからコマンドをクリックして操作します。  
  
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
  
2.  カーソルを置き`MethodB`メソッドの宣言またはメソッドの呼び出しで。  
  
3.  **リファクタリング** メニューのをクリックして**パラメーター順序の変更**します。  
  
     **パラメーター順序の変更** ダイアログ ボックスが表示されます。  
  
4.  **パラメーター順序の変更**ダイアログ ボックスで、`int i`で、**パラメーター**一覧、および下向きボタンをクリックします。  
  
     ドラッグする代わりに、`int i`後`bool b`で、**パラメーター**一覧。  
  
5.  **パラメーター順序の変更**ダイアログ ボックスで、をクリックして**OK**。  
  
     場合、**参照の変更のプレビュー**オプションが選択されて、**パラメーター順序の変更** ダイアログ ボックスで、**変更のプレビュー - パラメーター順序の変更** ダイアログ ボックスが表示されます。 パラメーター リストの変更のプレビュー`MethodB`シグネチャとメソッドの呼び出しの両方でします。  
  
    1.  場合、**変更のプレビュー - パラメーター順序の変更** ダイアログ ボックスが表示されたら、をクリックして**適用**します。  
  
         この例で、メソッドの宣言とすべてのメソッド呼び出しのサイト`MethodB`が更新されます。  
  
## <a name="remarks"></a>Remarks  
 メソッドの宣言またはメソッドの呼び出しからのパラメーターの順序を変更することができます。 メソッドまたはデリゲートの宣言の横にある、または本文ではなくにカーソルを置きます。  
  
## <a name="see-also"></a>関連項目  
 [リファクタリング (C#)](../csharp-ide/refactoring-csharp.md)