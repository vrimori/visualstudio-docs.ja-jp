---
title: インターフェイスの抽出リファクタリング (c#) |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.csharp.refactoring.extractinterface
dev_langs:
- CSharp
helpviewer_keywords:
- refactoring [C#], Extract Interface
- Extract Interface refactoring operation [C#]
ms.assetid: 7d0aa225-3b33-4331-9652-5a67cac6f3d0
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: e7c3af675155cf3d47d82457aadbfb6327895d4f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49279904"
---
# <a name="extract-interface-refactoring-c"></a>インターフェイスの抽出リファクタリング (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

インターフェイスの抽出は、既存のクラス、構造体、またはインターフェイスから発信されたメンバーを持つ新しいインターフェイスを作成する簡単な方法を提供するリファクタリング操作です。  
  
 いくつかのクライアントが同じクラス、構造体、またはインターフェイス メンバーのサブセットを使用する場合、または複数のクラス、構造体、またはインターフェイス メンバーのサブセットを共通のあるときに、インターフェイス内のメンバーのサブセットを具現化すると便利ですができます。 詳細については、インターフェイスを使用して、次を参照してください。[インターフェイス](http://msdn.microsoft.com/library/2feda177-ce11-432d-81b4-d50f5f35fd37)します。  
  
 インターフェイスの抽出では、新しいファイルにインターフェイスが生成され、新しいファイルの先頭にカーソルを位置付けます。 新しいインターフェイスや、新しいインターフェイスでの名前を使用して、生成されたファイルの名前を抽出するメンバーを指定することができます、**インターフェイスの抽出** ダイアログ ボックス。  
  
### <a name="to-use-extract-interface"></a>インターフェイスの抽出を使用するには  
  
1.  という名前のコンソール アプリケーションを作成する`ExtractInterface`、し、置き換えます`Program`を次のコード  
  
    ```csharp  
    // Invoke Extract Interface on ProtoA.  
    // Note:  the extracted interface will be created in a new file.  
    class ProtoA  
    {  
        public void MethodB(string s) { }  
    }  
    ```  
  
2.  カーソルが配置`MethodB`、 をクリック**インターフェイスの抽出**上、**リファクタリング**メニュー。  
  
     **インターフェイスの抽出** ダイアログ ボックスが表示されます。  
  
     キーボード ショートカット CTRL + R 表示を入力することも、**インターフェイスの抽出** ダイアログ ボックス。  
  
     マウスを右クリックすることもできますを指す**リファクタリング**、順にクリックします**インターフェイスの抽出**を表示する、**インターフェイスの抽出** ダイアログ ボックス。  
  
3.  クリックして**すべて選択**します。  
  
4.  **[OK]** をクリックします。  
  
     新しいファイルや IProtoA.cs、次のコードを参照してください。  
  
    ```csharp  
    using System;  
    namespace TopThreeRefactorings  
    {  
        interface IProtoA  
        {  
            void MethodB(string s);  
        }  
    }  
    ```  
  
## <a name="remarks"></a>Remarks  
 この機能は、クラス、構造体、またはインターフェイスに抽出するメンバーを含む、カーソルが置かれているときにのみアクセスできます。 この位置にカーソルがある場合は、インターフェイスの抽出リファクタリング操作を呼び出します。  
  
 クラスまたは構造体でインターフェイスの抽出を呼び出すと、基底クラスとインターフェイスの一覧は、新しいインターフェイス名を含めるに変更されます。 インターフェイスのインターフェイスの抽出を呼び出すときは、基底クラスとインターフェイスの一覧は変更されません。  
  
## <a name="see-also"></a>関連項目  
 [リファクタリング (C#)](../csharp-ide/refactoring-csharp.md)