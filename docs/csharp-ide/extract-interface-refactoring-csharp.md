---
redirect_url: /visualstudio/csharp-ide/refactoring/extract-interface
title: "インターフェイスの抽出リファクタリング (c#) |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: CSharp
helpviewer_keywords:
- refactoring [C#], Extract Interface
- Extract Interface refactoring operation [C#]
ms.assetid: 7d0aa225-3b33-4331-9652-5a67cac6f3d0
caps.latest.revision: "25"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: e3e606a86f5989ca928e0b093b564f997f92a559
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="extract-interface-refactoring-c"></a>インターフェイスの抽出リファクタリング (C#)
インターフェイスの抽出は、既存のクラス、構造体、またはインターフェイスから提供されるメンバーを持つ新しいインターフェイスを作成する簡単な方法を提供するリファクタリング操作です。  
  
 いくつかのクライアントが同じクラス、構造体、またはインターフェイス メンバーのサブセットを使用する場合、または複数のクラス、構造体、またはインターフェイス メンバーのサブセットに共通がある場合は、インターフェイスのメンバーのサブセットを具体化すると便利ですができます。 詳細については、インターフェイスを使用して、次を参照してください。[インターフェイス](/dotnet/csharp/programming-guide/interfaces/index)です。  
  
 インターフェイスの抽出は、新しいファイルでインターフェイスが生成され、新しいファイルの先頭にカーソルを位置付けます。 新しいインターフェイスや、新しいインターフェイスの名前を使用して、生成されたファイルの名前を抽出するメンバーを指定することができます、**インターフェイスの抽出** ダイアログ ボックス。  
  
### <a name="to-use-extract-interface"></a>インターフェイスの抽出を使用するには  
  
1.  というコンソール アプリケーションを作成`ExtractInterface`、し、置き換えます`Program`を次のコード  
  
    ```csharp  
    // Invoke Extract Interface on ProtoA.  
    // Note:  the extracted interface will be created in a new file.  
    class ProtoA  
    {  
        public void MethodB(string s) { }  
    }  
    ```  
  
2.  カーソルに置いた状態で`MethodB`、 をクリック**インターフェイスの抽出**上、**リファクター**メニュー。  
  
     **インターフェイスの抽出** ダイアログ ボックスが表示されます。  
  
     キーボード ショートカットを表示すれば、CTRL + R を入力することも、**インターフェイスの抽出** ダイアログ ボックス。  
  
     マウスを右クリックすることもできますをポイント**リファクター**、クリックして**インターフェイスの抽出**を表示する、**インターフェイスの抽出** ダイアログ ボックス。  
  
3.  をクリックして**すべて選択**です。  
  
4.  **[OK]**をクリックします。  
  
     新しいファイル、IProtoA.cs、および次のコードを参照してください。  
  
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
  
## <a name="remarks"></a>コメント  
 この機能をアクセス可能なは、クラス、構造体、またはインターフェイスを抽出するには、メンバーを含む、カーソルが置かれている場合だけです。 この位置にカーソルがある場合は、インターフェイスの抽出リファクタリング操作を呼び出します。  
  
 クラスまたは構造体でインターフェイスの抽出を呼び出すと、新しいインターフェイス名を含める基底クラスとインターフェイスの一覧が変更されます。 インターフェイスのインターフェイスの抽出を呼び出すと、基底クラスとインターフェイスのリストは変更されません。  
  
## <a name="see-also"></a>参照  
 [リファクタリング (C#)](refactoring-csharp.md)