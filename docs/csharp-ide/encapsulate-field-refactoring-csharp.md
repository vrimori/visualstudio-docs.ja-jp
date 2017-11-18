---
redirect_url: /visualstudio/csharp-ide/refactoring/encapsulate-field
title: "カプセル化 リファクタリング (c#) |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: CSharp
helpviewer_keywords:
- Encapsulate Field refactoring operation [C#]
- refactoring [C#], Encapsulate Field
ms.assetid: bf714a04-ab1e-49ce-99ce-dda1ebb1a17f
caps.latest.revision: "26"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7bd9e255b35ffb843c15d5ffa9c1547891bf437d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="encapsulate-field-refactoring-c"></a>フィールドのカプセル化リファクタリング (C#)
**フィールドのカプセル化**リファクタリング操作を使用すると、既存のフィールドからプロパティをすばやく作成し、新しいプロパティへの参照で、コードをシームレスに更新します。  
  
 ときに、[フィールド](/dotnet/csharp/programming-guide/classes-and-structs/fields)は[パブリック](/dotnet/csharp/language-reference/keywords/public)、他のオブジェクトのフィールドに直接アクセスおよび変更できますが、そのフィールドを所有するオブジェクトを検出します。 使用して[プロパティ](/dotnet/csharp/programming-guide/classes-and-structs/properties)そのフィールドをカプセル化するには、フィールドに直接アクセスを禁止できます。  
  
 新しいプロパティを作成する、**フィールドのカプセル化**操作をカプセル化するフィールドのアクセス修飾子を変更する[プライベート](/dotnet/csharp/language-reference/keywords/private)、し、生成[取得](/dotnet/csharp/language-reference/keywords/get)と[設定](/dotnet/csharp/language-reference/keywords/set)そのフィールドのアクセサー。 フィールドが読み取り専用で宣言されている場合など、`get` アクセサーだけが生成されることもあります。  
  
 リファクタリング エンジンで指定された領域で、新しいプロパティを参照しているコードを更新する、**更新参照**のセクションで、**フィールドのカプセル化** ダイアログ ボックス。  
  
### <a name="to-create-a-property-from-a-field"></a>フィールドからプロパティを作成するには  
  
1.  `EncapsulateFieldExample` という名前のコンソール アプリケーションを作成し、`Program` を次のコード例で置き換えます。  
  
    ```csharp  
    class Square  
    {  
        // Select the word 'width' and then use Encapsulate Field.  
        public int width, height;  
    }  
    class MainClass  
    {  
        public static void Main()  
        {  
            Square mySquare = new Square();  
            mySquare.width = 110;  
            mySquare.height = 150;  
            // Output values for width and height.  
            Console.WriteLine("width = {0}", mySquare.width);  
            Console.WriteLine("height = {0}", mySquare.height);  
        }  
    }  
    ```  
  
2.  [コード エディター](../ide/writing-code-in-the-code-and-text-editor.md)、カプセル化するフィールドの名前を宣言にカーソルを置きます。 次の例では、カーソルを `width` という語に移動します。  
  
    ```csharp  
    public int width, height;  
    ```  
  
3.  **リファクター**  メニューのをクリックして**フィールドのカプセル化**です。  
  
     **フィールドのカプセル化** ダイアログ ボックスが表示されます。  
  
     キーボード ショートカット ctrl キーを押しながら R キーを表示する電子メールを入力することも、**フィールドのカプセル化** ダイアログ ボックス。  
  
     カーソルを右クリックすることもできますをポイント**リファクター**、順にクリック**フィールドのカプセル化**を表示する、**フィールドのカプセル化** ダイアログ ボックス。  
  
4.  設定を指定します。  
  
5.  、ENTER キーを押すか、をクリックして、 **OK**ボタンをクリックします。  
  
6.  選択した場合、**参照の変更のプレビュー**オプション、**参照の変更のプレビュー**ウィンドウが開きます。 クリックして、**適用**ボタンをクリックします。  
  
     次の `get` アクセサー コードおよび `set` アクセサー コードがソース ファイルに表示されます。  
  
    ```csharp  
    public int Width  
    {  
        get { return width; }  
        set { width = value; }  
    }  
    ```  
  
     `Main` メソッドのコードも、新しい `Width` プロパティ名で更新されます。  
  
    ```csharp  
    Square mySquare = new Square();  
    mySquare.Width = 110;  
    mySquare.height = 150;  
    // Output values for width and height.  
    Console.WriteLine("width = {0}", mySquare.Width);  
    ```  
  
## <a name="remarks"></a>コメント  
 **フィールドのカプセル化**操作は、フィールドの宣言と同じ行にカーソルが配置されている場合にのみ可能です。  
  
 複数のフィールドを宣言できる宣言子の**フィールドのカプセル化**フィールドの間の境界としてコンマを使用し、最も近く、カーソルは、フィールド上と、そのカーソルと同じ行にリファクタリングを開始します。 宣言でフィールドの名前を選択することで、カプセル化するフィールドを指定することもできます。  
  
 このリファクタリング操作によって生成されるコードは、[フィールドのカプセル化] コード スニペット機能でモデル化されています。 コード スニペットは変更できます。 詳細については、「[Code Snippets](../ide/visual-csharp-code-snippets.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [リファクタリング (C#)](refactoring-csharp.md)   
 [Visual C# のコード スニペット](../ide/visual-csharp-code-snippets.md)