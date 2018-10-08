---
title: 名前の変更リファクタリング (c#) |Microsoft Docs
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
- vs.csharp.refactoring.rename
dev_langs:
- CSharp
helpviewer_keywords:
- refactoring [C#], Rename
- Rename refactoring [C#]
ms.assetid: 268942fc-b142-4dfa-8d90-bedd548c2e4f
caps.latest.revision: 45
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 8a70293719a70b7d4029f5c563aff30466368e00
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47549197"
---
# <a name="rename-refactoring-c"></a>名前の変更リファクタリング (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**名前を変更**リファクタリング機能など、フィールド、ローカル変数、メソッド、名前空間、プロパティ、および種類のコード シンボルの識別子の名前を変更する簡単な方法を提供する Visual Studio 統合開発環境 (IDE) です。 **名前を変更**コメントと文字列の名前を変更して、宣言と識別子の呼び出しを変更するために使用できます。  
  
> [!NOTE]
>  ソース管理 for Visual Studio を使用する場合は、名前の変更リファクタリングを実行する前に、ソースの最新バージョンを取得します。  
  
 名前の変更リファクタリングは、次の Visual Studio の機能から入手できます。  
  
|機能|IDE でのリファクタリングの動作|  
|-------------|----------------------------------------|  
|コード エディター|コード エディターでは、コード シンボルの特定の種類にカーソルを配置するときに名前の変更リファクタリングします。 カーソルがこの位置にあるときに呼び出すことができます、**の名前を変更**コマンドのキーボード ショートカット (CTRL + R, CTRL + R) を入力するかを選択して、**の名前を変更**からスマート タグ、ショートカット メニューのまたは、コマンド**リファクタリング**メニュー。|  
|クラス ビュー|クラス ビューで識別子を選択するとは、ショートカット メニューから使用可能な名前の変更リファクタリング、および**リファクタリング**メニュー。|  
|オブジェクト ブラウザー|オブジェクト ブラウザーで識別子を選択すると名前の変更リファクタリングがのみから使用可能な**リファクタリング**メニュー。|  
|Windows フォーム デザイナーのプロパティ グリッド|**プロパティ グリッド**Windows フォーム デザイナーのコントロールの名前を変更する操作が開始されます名前の変更を制御するのです。 **の名前を変更** ダイアログ ボックスが表示されません。|  
|ソリューション エクスプローラー|**ソリューション エクスプ ローラー**、**の名前を変更**コマンドがショートカット メニューで使用できます。 選択したソース ファイルにファイル名と同じクラス名を持つクラスが含まれている場合は、同時にソース ファイルの名前し、名前の変更リファクタリングを実行するこのコマンドを使用できます。<br /><br /> たとえば、既定の Windows ベースのアプリケーションを作成し、Form1.cs TestForm.cs に名前を変更する場合 Form1.cs はソース ファイルの名前に変更 TestForm.cs を Form1 クラスおよびクラスは TestForm に名前を変更することへの参照すべて。 **注:** 、**を元に戻す**コマンド (CTRL + Z) の名前の変更のリファクタリング、コードで元に戻すし、ファイル名が元の名前を変更しないのは、のみです。 <br /><br /> 選択したソース ファイルには、ファイル名と同じ名前のクラスが含まれていない場合、**の名前を変更**コマンド**ソリューション エクスプ ローラー**ソース ファイルの名前のみが、名前の変更は実行されませんリファクタリング。|  
  
## <a name="rename-operations"></a>名前変更の操作  
 実行時に**の名前を変更**、リファクタリング、エンジンは、次の表に示すように、各コード シンボルの特定の名前の変更操作を実行します。  
  
|コード シンボル|操作の名前を変更します。|  
|-----------------|----------------------|  
|フィールド|新しい名前を宣言し、フィールドの使用法を変更します。|  
|ローカル変数|新しい名前に、宣言と変数の使用法を変更します。|  
|メソッド|新しい名前に、メソッドとそのメソッドに対するすべての参照の名前を変更します。 **注:** メソッドの拡張メソッドが静的メソッドまたはインスタンス メソッドとして使用されているかどうかに関係なく、スコープ内のすべてのインスタンスに拡張メソッドの名前を変更するときに名前変更操作が反映されます。 詳細については、「[拡張メソッド](http://msdn.microsoft.com/library/175ce3ff-9bbf-4e64-8421-faeb81a0bb51)」を参照してください。|  
|名前空間|名前空間の名前を宣言で、新しい名前に変更すべて`using`ステートメント、および完全修飾名。 **注:** 名前空間の名前を変更するときに[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]も更新、**既定 Namespace**プロパティを**アプリケーション**のページ、**プロジェクト デザイナー**. このプロパティを選択してリセットすることはできません**を元に戻す**から、**編集**メニュー。 リセット、**既定 Namespace**プロパティの値でプロパティを変更する必要があります、**プロジェクト デザイナー**します。 詳細については、次を参照してください。[アプリケーション ページ](../ide/reference/application-page-project-designer-csharp.md)します。|  
|プロパティ|新しい名前を宣言し、プロパティの使用法を変更します。|  
|型|すべての宣言と型のすべての使用状況をコンス トラクターとデストラクターを含む、新しい名前に変更します。 部分の型の名前の変更操作は、すべての部分に反映されます。|  
  
#### <a name="to-rename-an-identifier"></a>識別子の名前を変更するには  
  
1.  `RenameIdentifier` という名前のコンソール アプリケーションを作成し、`Program` を次のコード例で置き換えます。  
  
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
  
3.  **リファクタリング**メニューの **の名前を変更**します。 **の名前を変更** ダイアログ ボックスが表示されます。  
  
     カーソルを右クリックして をポイント**リファクタリング** をクリックし、コンテキスト メニューで**の名前を変更**を表示する、**の名前を変更** ダイアログ ボックス。  
  
4.  **新しい名前**フィールドに「`MethodC`します。  
  
5.  選択、**コメント内の検索**チェック ボックスをオンします。  
  
6.  **[OK]** をクリックします。  
  
7.  **変更のプレビュー**ダイアログ ボックスで、をクリックして**適用**します。  
  
#### <a name="to-rename-an-identifier-using-smart-tags"></a>スマート タグを使用して識別子の名前を変更するには  
  
1.  `RenameIdentifier` という名前のコンソール アプリケーションを作成し、`Program` を次のコード例で置き換えます。  
  
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
  
2.  宣言で`MethodB`入力するか、backspace キーでメソッドの識別子。 スマート タグのプロンプトは、この識別子の下に表示されます。  
  
    > [!NOTE]
    >  名前の変更リファクタリング スマート タグを使用した識別子の宣言でのみ起動できます。  
  
3.  SHIFT + ALT + F10 キーボード ショートカットを入力して、スマート タグ メニューを表示する下方向キーを押します。  
  
     - または -  
  
     スマート タグの表示にスマート タグのプロンプト上には、マウス ポインターを移動します。 スマート タグの上にマウス ポインターを移動し、スマート タグ メニューを表示する下矢印をクリックします。  
  
4.  選択、**の名前を変更 '\<identifer1 >' を'\<identifier2 >'** のコードの変更のプレビューを使用しない名前の変更のリファクタリングを開始するメニュー項目。 すべての参照を **\<identifer1 >** に自動的に更新が **\<identifier2 >** します。  
  
     - または -  
  
     選択、**をプレビュー**コードの変更のプレビューでの名前の変更リファクタリングを開始するメニュー項目。 **変更のプレビュー**  ダイアログ ボックスが表示されます。  
  
## <a name="remarks"></a>Remarks  
  
## <a name="renaming-implemented-or-overridden-members"></a>実装またはオーバーライドされたメンバーの名前を変更します。  
 ときにする**の名前を変更**実装/オーバーライドまたは他の種類のメンバーによって実装またはオーバーライドされるメンバー[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]という名前の変更操作がカスケード更新を発生 ダイアログ ボックスが表示されます。 クリックすると**続行**、リファクタリング エンジン再帰的に検索し、ベースのすべてのメンバーの名前を変更および派生型を持つ実装/上書きリレーションシップ、メンバーの名前が変更されるとします。  
  
 次のコード例には、実装またはオーバーライドのリレーションシップを持つメンバーが含まれています。  
  
 [!code-csharp[CsUsingCsIDERefactor#1](../snippets/csharp/VS_Snippets_VBCSharp/CsUsingCsIDERefactor/CS/Class1.cs#1)]  
  
 前の例では、名前を変更する`C.Method()`名前も変更`Ibase.Method()`ため`C.Method()`実装`Ibase.Method()`。 次に、リファクタリング エンジンを再帰的には`Ibase.Method()`によって実装される`Derived.Method()`の名前を変更および`Derived.Method()`。 リファクタリング エンジン名前は変更されません`Base.Method()`ため、`Derived.Method()`をオーバーライドしない`Base.Method()`します。 リファクタリング エンジンはない限り、ここで停止**オーバー ロードの名前を変更**チェックイン、**の名前を変更** ダイアログ ボックス。  
  
 場合**オーバー ロードの名前を変更**リファクタリング エンジンの名前を変更、チェック`Derived.Method(int i)`オーバー ロードするため`Derived.Method()`、`Base.Method(int i)`によってオーバーライドされますので`Derived.Method(int i)`、および`Base.Method()`のオーバー ロードがあるためです`Base.Method(int i)`.  
  
> [!NOTE]
>  参照されたアセンブリで定義されたメンバーの名前を変更すると、ダイアログ ボックスでは、名前を変更すると、ビルド エラーが発生するについて説明します。  
  
## <a name="renaming-properties-of-anonymous-types"></a>匿名型のプロパティの名前を変更します。  
 匿名型のプロパティの名前を変更するときに、名前の変更操作は、同じプロパティを持つ匿名型を他のプロパティに反映されます。 次の例では、この動作を示します。  
  
```csharp  
var a = new { ID = 1};  
var b = new { ID = 2};  
```  
  
 上記のコードで名前を変更する`ID`変わります`ID`両方のステートメントで同じ基になる匿名型があるため。  
  
```csharp  
var companyIDs =  
    from c in companylist  
    select new { ID = c.ID, Name = c.Name};  
  
var orderIDs =  
    from o in orderlist  
    select new { ID = o.ID, Item = o.Name};  
```  
  
 上記のコードで名前を変更する`ID`の 1 つのインスタンスの名前を変更のみが`ID`ため`companyIDs`と`orderIDs`は同じプロパティがありません。  
  
## <a name="see-also"></a>関連項目  
 [リファクタリング (C#)](../csharp-ide/refactoring-csharp.md)   
 [匿名型](http://msdn.microsoft.com/library/59c9d7a4-3b0e-475e-b620-0ab86c088e9b)