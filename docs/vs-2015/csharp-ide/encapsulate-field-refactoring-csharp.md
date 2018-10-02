---
title: カプセル化 リファクタリング (c#) |Microsoft Docs
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
- vs.csharp.refactoring.encapsulatefield
dev_langs:
- CSharp
helpviewer_keywords:
- Encapsulate Field refactoring operation [C#]
- refactoring [C#], Encapsulate Field
ms.assetid: bf714a04-ab1e-49ce-99ce-dda1ebb1a17f
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 882ee68a1a5127cd46ff8ce5b6ea3350c95c6e8a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47538647"
---
# <a name="encapsulate-field-refactoring-c"></a>フィールドのカプセル化リファクタリング (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**フィールドのカプセル化**リファクタリング操作を使用すると、既存のフィールドからプロパティをすばやく作成し、新規プロパティへの参照で、コードをシームレスに更新します。  
  
 ときに、[フィールド](http://msdn.microsoft.com/library/3cbb2f61-75f8-4cce-b4ef-f5d1b3de0db7)は[パブリック](http://msdn.microsoft.com/library/0ae45d16-a551-4b74-9845-57208de1328e)、他のオブジェクトがそのフィールドに直接アクセスおよび変更できますが、そのフィールドを所有するオブジェクトが検出されません。 使用して[プロパティ](http://msdn.microsoft.com/library/e295a8a2-b357-4ee7-a12e-385a44146fa8)そのフィールドをカプセル化するには、フィールドに直接アクセスを禁止できます。  
  
 新しいプロパティを作成する、**フィールドのカプセル化**操作をカプセル化するフィールドのアクセス修飾子を変更する[プライベート](http://msdn.microsoft.com/library/654c0bb8-e6ac-4086-bf96-7474fa6aa1c8)、し、生成[取得](http://msdn.microsoft.com/library/a52de048-fbe0-41b0-82ec-8e4ac04d3a71)と[設定](http://msdn.microsoft.com/library/30d7e4e5-cc2e-4635-a597-14a724879619)そのフィールドのアクセサー。 フィールドが読み取り専用で宣言されている場合など、`get` アクセサーだけが生成されることもあります。  
  
 リファクタリング エンジンで指定された領域で、新しいプロパティを参照しているコードが更新、**参照の更新**のセクション、**フィールドのカプセル化** ダイアログ ボックス。  
  
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
  
3.  **リファクタリング** メニューのをクリックして**フィールドのカプセル化**します。  
  
     **フィールドのカプセル化** ダイアログ ボックスが表示されます。  
  
     キーボード ショートカット CTRL + R を表示する電子メールを入力することも、**フィールドのカプセル化** ダイアログ ボックス。  
  
     カーソルを右クリックして をポイント**リファクタリング**、順にクリックします**フィールドのカプセル化**を表示する、**フィールドのカプセル化** ダイアログ ボックス。  
  
4.  設定を指定します。  
  
5.  ENTER を押すか、クリックして、 **OK**ボタンをクリックします。  
  
6.  選択した場合、**参照の変更のプレビュー**オプション、**参照の変更のプレビュー**ウィンドウが開きます。 をクリックして、**適用**ボタンをクリックします。  
  
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
  
## <a name="remarks"></a>Remarks  
 **フィールドのカプセル化**操作は、フィールドの宣言と同じ行にカーソルが配置されている場合にのみ可能です。  
  
 複数のフィールドの宣言に**フィールドのカプセル化**フィールド間の区切りとしてコンマを使用し、最も近く、カーソルであるフィールドでは、そのカーソルと同じ行にリファクタリングを開始します。 宣言でフィールドの名前を選択することで、カプセル化するフィールドを指定することもできます。  
  
 このリファクタリング操作によって生成されるコードは、[フィールドのカプセル化] コード スニペット機能でモデル化されています。 コード スニペットは変更できます。 詳細については、「[Code Snippets](../ide/code-snippets.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [リファクタリング (C#)](../csharp-ide/refactoring-csharp.md)   
 [Visual C# のコード スニペット](../ide/visual-csharp-code-snippets.md)