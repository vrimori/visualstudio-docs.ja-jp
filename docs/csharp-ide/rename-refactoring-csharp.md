---
redirect_url: /visualstudio/csharp-ide/refactoring/rename
title: "名前の変更リファクタリング (c#) |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: CSharp
helpviewer_keywords:
- refactoring [C#], Rename
- Rename refactoring [C#]
ms.assetid: 268942fc-b142-4dfa-8d90-bedd548c2e4f
caps.latest.revision: "45"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: 42c5f99b3bf5ba95bc279cd5e117745ccc8e02c3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="rename-refactoring-c"></a>名前の変更リファクタリング (C#)
**名前を変更**フィールド、ローカル変数、メソッド、名前空間、プロパティ、および種類などのコードのシンボルの識別子の名前を変更する簡単な方法を提供する Visual Studio 統合開発環境 (IDE) のリファクタリング機能です。 **名前を変更**コメントや文字列で名前を変更して、宣言と識別子の呼び出しを変更するために使用できます。  
  
> [!NOTE]
>  ソース管理 for Visual Studio を使用する場合は、名前の変更リファクタリングを実行しようとする前に、ソースの最新バージョンを取得します。  
  
 名前の変更リファクタリングは、次の Visual Studio の機能から入手できます。  
  
|機能|IDE でのリファクタリングの動作|  
|-------------|----------------------------------------|  
|コード エディター|コード エディターでは、特定の種類のコードのシンボルにカーソルを配置するときに使用可能な名前の変更リファクタリングです。 この位置にカーソルがある場合を呼び出すことができます、**の名前を変更**コマンドのキーボード ショートカット (Ctrl + R、Ctrl + R) を入力するかを選択して、**の名前を変更**クイック アクション、ショートカット メニューからコマンド、または**リファクター**メニュー。|  
|クラス ビュー|クラス ビューで識別子を選択する場合は、ショートカット メニューから使用可能な名前の変更リファクタリングと**リファクター**メニュー。|  
|オブジェクト ブラウザー|オブジェクト ブラウザーで識別子を選択すると名前の変更リファクタリングは、のみから使用可能な**リファクター**メニュー。|  
|Windows フォーム デザイナーのプロパティ グリッド|**プロパティ グリッド**Windows フォーム デザイナーのコントロールの名前を変更する操作が開始されます名前の変更を制御するためです。 **の名前を変更** ダイアログ ボックスは表示されません。|  
|ソリューション エクスプローラー|**ソリューション エクスプ ローラー**、**の名前を変更**コマンドがショートカット メニューを使用します。 選択したソース ファイルには、ファイル名と同じクラス名を持つクラスが含まれている場合は、同時に、ソース ファイルの名前を変更し、名前の変更リファクタリングを実行するこのコマンドを使用できます。<br /><br /> たとえば、既定の Windows ベースのアプリケーションを作成して、Form1.cs TestForm.cs に名前を変更ソース ファイル名 Form1.cs は TestForm.cs を Form1 クラスと変更のすべての参照をクラスは TestForm に名前を変更することです。 **注:** 、**を元に戻す**コマンド (CTRL + Z) の名前の変更がコードのリファクタリングを元に戻すし、ファイル名がバックアップ元の名前に変更しないはのみです。 <br /><br /> 選択したソース ファイルには、ファイル名と同じ名前のクラスが含まれていない場合、**の名前を変更**コマンド**ソリューション エクスプ ローラー**ソース ファイルの名前のみが、名前の変更は実行されませんリファクタリングしてください。|  
  
## <a name="rename-operations"></a>名前変更の操作  
 実行すると**の名前を変更**、リファクタリング エンジンは、次の表に示すようにコードのシンボルごとに、特定の名前を変更する操作を実行します。  
  
|コードのシンボル|操作の名前を変更します。|  
|-----------------|----------------------|  
|フィールド|新しい名前に、宣言とフィールドの使用法を変更します。|  
|ローカル変数|新しい名前に、宣言と変数の使用法を変更します。|  
|メソッド|新しい名前に、メソッドとそのメソッドにすべての参照の名前を変更します。 **注:**メソッドの拡張メソッドを静的メソッドまたはインスタンス メソッドとして使用されているかどうかに関係なく、スコープ内にあるすべてのインスタンスに名前の変更操作が反映される拡張メソッドの名前を変更するときにします。 詳細については、「[拡張メソッド](/dotnet/csharp/programming-guide/classes-and-structs/extension-methods)」を参照してください。|  
|名前空間|宣言では、新しい名前に、名前空間の名前を変更すべて`using`ステートメント、および完全修飾名。 **注:**名前空間の名前を変更するときに[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]も更新、 **Default Namespace**プロパティを**アプリケーション**のページ、**プロジェクト デザイナー**. 選択すると、このプロパティをリセットできません**を元に戻す**から、**編集**メニュー。 リセットする、 **Default Namespace**プロパティの値でプロパティを変更する必要があります、**プロジェクト デザイナー**です。 詳細については、次を参照してください。[アプリケーション ページ](../ide/reference/application-page-project-designer-csharp.md)です。|  
|プロパティ|新しい名前を指定するには、宣言とプロパティの使用法を変更します。|  
|型|すべての宣言と型のすべての使用状況をコンス トラクターとデストラクターを含む、新しい名前に変更します。 部分型の場合は、名前の変更操作はすべての部分に反映されます。|  
  
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
  
2.  カーソルを置き`MethodB`メソッドの宣言またはメソッドの呼び出しのいずれか。  
  
3.  **リファクター**メニューの **の名前を変更**です。 **の名前を変更** ダイアログ ボックスが表示されます。  
  
     カーソルを右クリックすることができますも をポイント**リファクター**をクリックしてコンテキスト メニューで、**の名前を変更**を表示する、**の名前を変更** ダイアログ ボックス。  
  
4.  **新しい名前**フィールドに「`MethodC`です。  
  
5.  選択、**コメント内の検索**チェック ボックスをオンします。  
  
6.  **[OK]**をクリックします。  
  
7.  **変更のプレビュー**ダイアログ ボックスで、をクリックして**適用**です。  
  
#### <a name="to-rename-an-identifier-using-quick-actions"></a>クイック アクションを使用する識別子の名前を変更するには  
  
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
  
2.  宣言内`MethodB`入力、または backspace キーでメソッドの識別子。 クイック アクション電球は、余白に表示されます。  
  
    > [!NOTE]
    >  名前の変更リファクタリング クイック操作を使用して、識別子の宣言でのみ起動できます。  
  
3.  キーボード ショートカット**shift キーを押しながら Alt キーを押しながら F10**クイック アクション メニューを表示します。  
  
     - または -  
  
     クイック アクション メニューを表示する電球の横にある黒い三角形をクリックします。  
  
4.  選択、**の名前を変更 '\<identifer1 >' に'\<identifier2 >'**名前の変更リファクタリングを起動するメニュー項目。 すべての参照を **\<identifer1 >**に自動的に更新されます **\<identifier2 >**です。  
  
## <a name="remarks"></a>コメント  
  
## <a name="renaming-implemented-or-overridden-members"></a>実装またはオーバーライドされたメンバーの名前を変更します。  
 ときにする**の名前を変更**か、実装またはオーバーライドまたはその他の型のメンバーによって実装またはオーバーライドされるメンバー[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]という名前の変更操作が発生するカスケード更新 ダイアログ ボックスが表示されます。 クリックすると**続行**、リファクタリング エンジン再帰的に検索し、ベース内のすべてのメンバーの名前を変更とを持つ派生型を実装して/上書きリレーションシップ、メンバーの名前を変更するとします。  
  
 次のコード例には、実装またはオーバーライドのリレーションシップを持つメンバーが含まれています。  
  
 [!code-csharp[CsUsingCsIDERefactor#1](../csharp-ide/codesnippet/CSharp/rename-refactoring-csharp_1.cs)]  
  
 前の例では、名前を変更する`C.Method()`名前も変更`Ibase.Method()`ため`C.Method()`実装`Ibase.Method()`です。 次に、エンジンをリファクターする再帰的にされることを確認`Ibase.Method()`によって実装される`Derived.Method()`の名前を変更および`Derived.Method()`です。 リファクター エンジンは、名前は変更されません`Base.Method()`ので、`Derived.Method()`をオーバーライドしません`Base.Method()`です。 ない限り、リファクタリングのエンジンはここで停止**オーバー ロードの名前を変更**チェックイン、**の名前を変更** ダイアログ ボックス。  
  
 場合**オーバー ロードの名前を変更**リファクター エンジンの名前を変更、チェック`Derived.Method(int i)`オーバー ロードするため`Derived.Method()`、`Base.Method(int i)`によってオーバーライドされますので`Derived.Method(int i)`、および`Base.Method()`のオーバー ロードになっているため`Base.Method(int i)`.  
  
> [!NOTE]
>  参照されたアセンブリで定義されたメンバーの名前を変更するときに、ダイアログ ボックスでは、名前を変更すると、ビルド エラーが発生するについて説明します。  
  
## <a name="renaming-properties-of-anonymous-types"></a>匿名型のプロパティの名前を変更します。  
 匿名型のプロパティの名前を変更するときに、名前の変更操作は、他の同じプロパティを持つ匿名型のプロパティに反映されます。 次の例では、この動作を示します。  
  
```csharp  
var a = new { ID = 1};  
var b = new { ID = 2};  
```  
  
 上記のコードでは、名前を変更する`ID`変わります`ID`両方のステートメントで同じ基になる匿名型があるためです。  
  
```csharp  
var companyIDs =  
    from c in companylist  
    select new { ID = c.ID, Name = c.Name};  
  
var orderIDs =  
    from o in orderlist  
    select new { ID = o.ID, Item = o.Name};  
```  
  
 上記のコードでは、名前を変更する`ID`の 1 つのインスタンスの名前を変更のみが`ID`ため`companyIDs`と`orderIDs`は同じプロパティがありません。  
  
## <a name="see-also"></a>参照  
 [リファクタリング (C#)](refactoring-csharp.md)   
 [匿名型](/dotnet/csharp/programming-guide/classes-and-structs/anonymous-types)