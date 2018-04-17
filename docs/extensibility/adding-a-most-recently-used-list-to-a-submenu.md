---
title: 最近使用したサブメニューの一覧を追加する |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- MRU lists
- menus, creating MRU list
- most recently used
ms.assetid: 27d4bbcf-99b1-498f-8b66-40002e3db0f8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 67eb08feff5d8edd1251c8fcff09d8f148b51b96
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="adding-a-most-recently-used-list-to-a-submenu"></a>サブメニューの一覧を使用して、ほとんどの最近追加
このチュートリアルのデモンストレーションに基づいて[メニューにサブメニューを追加](../extensibility/adding-a-submenu-to-a-menu.md)サブメニューに動的な一覧を追加する方法を示しています。 動的な一覧は、最も最近使用した (MRU) のリストの作成の基礎を形成します。  
  
 動的メニュー リストは、メニュー上のプレース ホルダーを開始します。 たびに、メニューを表示すると、Visual Studio 統合開発環境 (IDE) がプレース ホルダーに表示されるすべてのコマンド、VSPackage が求められます。 動的な一覧は、メニューのどこにでも存在ことができます。 ただし、動的なリストは通常格納され、サブメニュー、またはメニューの下部にある、単独で表示します。 これらの設計パターンを使用して、動的コマンドの一覧を展開し、メニューには、他のコマンドの位置の影響を与えずにコントラクトが有効にします。 このチュートリアルでは、サブメニューの残りの部分から 1 行で区切られた、既存のサブメニューの下部にある動的な MRU 一覧が表示されます。  
  
 技術的には、動的な一覧は、ツールバーにも適用できます。 ただし、お勧めしませんその使用法ツールバーのままにしない限り、ユーザーがこれを変更する特定の手順を実行しているためです。  
  
 このチュートリアルで作成、その順序を変更するたびに、それらの 1 つが選択されている 4 つの項目のリストの MRU (選択した項目はリストの先頭に移動します)。  
  
 メニューと .vsct ファイルの詳細については、次を参照してください。[コマンド、メニュー、およびツールバー](../extensibility/internals/commands-menus-and-toolbars.md)です。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルに従うには、Visual Studio SDK をインストールする必要があります。 詳細については、次を参照してください。 [Visual Studio SDK](../extensibility/visual-studio-sdk.md)です。  
  
## <a name="creating-an-extension"></a>拡張機能の作成  
  
-   次の手順では、[メニューにサブメニューを追加](../extensibility/adding-a-submenu-to-a-menu.md)を次の手順で変更されるサブメニューを作成します。  
  
 このチュートリアルの手順では、VSPackage の名前があると仮定`TopLevelMenu`で使用されている名前は[Visual Studio のメニュー バーにメニューを追加する](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)です。  
  
## <a name="creating-a-dynamic-item-list-command"></a>動的項目一覧のコマンドを作成します。  
  
1.  TestCommandPackage.vsct を開きます。  
  
2.  `Symbols`セクションで、 `GuidSymbol` guidTestCommandPackageCmdSet、という名前のノード追加のシンボルは、`MRUListGroup`グループおよび`cmdidMRUList`コマンドを次のようにします。  
  
    ```csharp  
    <IDSymbol name="MRUListGroup" value="0x1200"/>  
    <IDSymbol name="cmdidMRUList" value="0x0200"/>  
    ```  
  
3.  `Groups`セクションで、既存のグループのエントリ後に、宣言されたグループを追加します。  
  
    ```cpp  
    <Group guid="guidTestCommandPackageCmdSet" id="MRUListGroup"   
           priority="0x0100">  
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenu"/>  
    </Group>  
  
    ```  
  
4.  `Buttons`セクションで、ボタンの既存のエントリの後に、新規に宣言されるコマンドを表すノードを追加します。  
  
    ```csharp  
    <Button guid="guidTestCommandPackageCmdSet" id="cmdidMRUList"  
        type="Button" priority="0x0100">  
        <Parent guid="guidTestCommandPackageCmdSet" id="MRUListGroup" />  
        <CommandFlag>DynamicItemStart</CommandFlag>  
        <Strings>  
            <CommandName>cmdidMRUList</CommandName>  
            <ButtonText>MRU Placeholder</ButtonText>  
                </Strings>  
    </Button>  
    ```  
  
     `DynamicItemStart`フラグを動的に生成するコマンドを使用できます。  
  
5.  プロジェクトをビルドし、新しいコマンドのディスプレイをテストするデバッグを開始します。  
  
     **TestMenu** ] メニューの [新しいサブメニューをクリックして**サブメニュー**新しいコマンドを表示するには、 **MRU プレース ホルダー**です。 コマンドの動的な MRU 一覧は、次の手順では後、は、そのリストによってたびにサブメニューが開かれているときに、このコマンドのラベルが置き換えられます。  
  
## <a name="filling-the-mru-list"></a>MRU 一覧を入力  
  
1.  TestCommandPackageGuids.cs、内の既存のコマンド Id の後に次の行を追加、`TestCommandPackageGuids`クラス定義です。  
  
    ```csharp  
    public const string guidTestCommandPackageCmdSet = "00000000-0000-0000-0000-00000000"; // get the GUID from the .vsct file  
    public const uint cmdidMRUList = 0x200;  
    ```  
  
2.  TestCommand.cs で次のコードを追加ステートメントを使用します。  
  
    ```csharp  
    using System.Collections;  
    ```  
  
3.  AddCommand の最後の呼び出し後、TestCommand コンス トラクターで、次のコードを追加します。 `InitMRUMenu`後で定義されています。  
  
    ```csharp  
    this.InitMRUMenu(commandService);  
    ```  
  
4.  TestCommand クラスでは、次のコードを追加します。 このコードでは、MRU 一覧に表示する項目を表す文字列のリストを初期化します。  
  
    ```csharp  
    private int numMRUItems = 4;  
    private int baseMRUID = (int)TestCommandPackageGuids.cmdidMRUList;  
    private ArrayList mruList;  
  
    private void InitializeMRUList()  
    {  
        if (null == this.mruList)  
        {  
            this.mruList = new ArrayList();  
            if (null != this.mruList)  
            {  
                for (int i = 0; i < this.numMRUItems; i++)  
                {  
                    this.mruList.Add(string.Format(CultureInfo.CurrentCulture,  
                        "Item {0}", i + 1));  
                }  
            }  
        }  
    }  
    ```  
  
5.  後に、`InitializeMRUList`メソッドを追加、`InitMRUMenu`メソッドです。 これには、MRU 一覧のメニュー コマンドを初期化します。  
  
    ```csharp  
    private void InitMRUMenu(OleMenuCommandService mcs)  
    {  
        InitializeMRUList();  
        for (int i = 0; i < this.numMRUItems; i++)  
        {  
            var cmdID = new CommandID(  
                new Guid(TestCommandPackageGuids.guidTestCommandPackageCmdSet), this.baseMRUID + i);  
            var mc = new OleMenuCommand(  
                new EventHandler(OnMRUExec), cmdID);  
            mc.BeforeQueryStatus += new EventHandler(OnMRUQueryStatus);  
            mcs.AddCommand(mc);  
        }  
    }  
    ```  
  
     MRU 一覧にすべての可能な項目のメニュー コマンド オブジェクトを作成する必要があります。 IDE の呼び出し、`OnMRUQueryStatus`がこれ以上項目まで MRU 一覧内の各項目のメソッドです。 マネージ コードでは、最初に使用可能なすべての項目を作成するこれ以上項目があることを確認するための IDE にしかありません。 する場合は、追加、アイテムをマークで非表示として最初を使用して`mc.Visible = false;`メニュー コマンドの作成後にします。 これらの項目から表示できる以降を使用して`mc.Visible = true;`で、`OnMRUQueryStatus`メソッドです。  
  
6.  後に、`InitMRUMenu`メソッドでは、次の追加`OnMRUQueryStatus`メソッドです。 これは、各最近使用した項目のテキストを設定するハンドラーです。  
  
    ```csharp  
    private void OnMRUQueryStatus(object sender, EventArgs e)  
    {  
        OleMenuCommand menuCommand = sender as OleMenuCommand;  
        if (null != menuCommand)  
        {  
            int MRUItemIndex = menuCommand.CommandID.ID - this.baseMRUID;  
            if (MRUItemIndex >= 0 && MRUItemIndex < this.mruList.Count)  
            {  
                menuCommand.Text = this.mruList[MRUItemIndex] as string;  
            }  
        }  
    }  
    ```  
  
7.  後に、`OnMRUQueryStatus`メソッドでは、次の追加`OnMRUExec`メソッドです。 これは、最近使用した項目を選択するためのハンドラーです。 このメソッドは、選択した項目を一覧の一番上に移動し、メッセージ ボックスに、選択した項目を表示します。  
  
    ```csharp  
    private void OnMRUExec(object sender, EventArgs e)  
    {  
        var menuCommand = sender as OleMenuCommand;  
        if (null != menuCommand)  
        {  
            int MRUItemIndex = menuCommand.CommandID.ID - this.baseMRUID;  
            if (MRUItemIndex >= 0 && MRUItemIndex < this.mruList.Count)  
            {  
                string selection = this.mruList[MRUItemIndex] as string;  
                for (int i = MRUItemIndex; i > 0; i--)  
                {  
                    this.mruList[i] = this.mruList[i - 1];  
                }  
                this.mruList[0] = selection;  
                System.Windows.Forms.MessageBox.Show(  
                    string.Format(CultureInfo.CurrentCulture,  
                                  "Selected {0}", selection));  
            }  
        }  
    }  
  
    ```  
  
## <a name="testing-the-mru-list"></a>MRU 一覧のテスト  
  
#### <a name="to-test-the-mru-menu-list"></a>MRU メニュー リストをテストするには  
  
1.  プロジェクトのビルドし、デバッグの開始  
  
2.  **TestMenu**  メニューのをクリックして**呼び出す TestCommand**です。 これには、コマンドが選択されていることを示すメッセージ ボックスが表示されます。  
  
    > [!NOTE]
    >  読み込んで正しく MRU 一覧を表示する VSPackage を強制するには、この手順が必要です。 この手順をスキップする場合は、MRU 一覧は表示されません。  
  
3.  **テスト メニュー**  メニューのをクリックして**サブメニュー**です。 4 つの項目の一覧は、区切り記号の下のサブメニューの最後に表示されます。 クリックすると、**項目 3**、メッセージ ボックスが表示され、「選択された項目 3」のテキストを表示する必要があります。 (4 つの項目の一覧が表示されない場合を確認して前の手順の指示に従っていること。)  
  
4.  サブメニューをもう一度開きます。 注意して**項目 3**一覧の上部にあるようになりましたが、他のアイテムが下の 1 つの位置にプッシュされているとします。 をクリックして**項目 3**再度とメッセージ ボックスに「選択された項目 3」が表示されているテキストが正しくコマンド ラベルと共に新しい位置に移動したことを示します。  
  
## <a name="see-also"></a>関連項目  
 [メニュー項目の動的な追加](../extensibility/dynamically-adding-menu-items.md)