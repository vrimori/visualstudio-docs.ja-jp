---
title: "サブメニューにリストを使用する最近のほとんどを追加します。 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MRU 一覧"
  - "メニュー、MRU 一覧を作成します。"
  - "最近使った"
ms.assetid: 27d4bbcf-99b1-498f-8b66-40002e3db0f8
caps.latest.revision: 46
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 46
---
# サブメニューにリストを使用する最近のほとんどを追加します。
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

このチュートリアルのデモンストレーションに基づき [メニューのサブメニューの追加](../extensibility/adding-a-submenu-to-a-menu.md), 、サブメニューに動的な一覧を追加する方法を示しています。 動的な一覧は、最も最近使用した\) リストを作成するための基礎を形成します。  
  
 動的メニューの一覧は、メニュー上のプレース ホルダーで開始されます。 メニューが表示されるたびに、Visual Studio 統合開発環境 \(IDE\) がプレース ホルダーに表示されるすべてのコマンドを VSPackage を要求します。 動的な一覧は、メニューのどこにでも存在ことができます。 ただし、動的リストは通常格納されているし、サブメニューやメニューの下部で、単独で表示されます。 これらのデザイン パターンを使用すると、デプロイメントし、その他のメニューのコマンドの位置の影響を与えずに縮小するためのコマンドの動的な一覧を有効にします。 このチュートリアルでは、既存のサブメニューを行によって、サブメニューの残りの部分から分離の下部にある動的な MRU 一覧が表示されます。  
  
 技術的には、動的な一覧は、ツールバーにも適用できます。 ただし、使用状況は、ツールバーのままにしない限り、ユーザーが特定の手順を変更するためお防止します。  
  
 このチュートリアルは、その順序を変更するたびにそれらの 1 つが選択されている 4 つの項目の MRU 一覧を作成 \(選択した項目はリストの先頭に移動します\)。  
  
 メニューおよび .vsct ファイルの詳細については、次を参照してください。 [コマンド、メニューのおよびツールバー](../extensibility/internals/commands-menus-and-toolbars.md)します。  
  
## 必須コンポーネント  
 このチュートリアルを行うには、Visual Studio SDK をインストールする必要があります。 詳細については、「[Visual Studio SDK](../extensibility/visual-studio-sdk.md)」を参照してください。  
  
## 拡張機能の作成  
  
-   次の手順では、 [メニューのサブメニューの追加](../extensibility/adding-a-submenu-to-a-menu.md) を次の手順で変更されるサブメニューを作成します。  
  
 このチュートリアルでは、この手順では、VSPackage の名前があると想定 `TopLevelMenu`, で使用されている名前である [Visual Studio のメニュー バーにメニューを追加します。](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)です。  
  
## 動的な項目\] ボックスの一覧のコマンドを作成します。  
  
1.  TestCommandPackage.vsct を開きます。  
  
2.  `Symbols` セクションで、 `GuidSymbol` guidTestCommandPackageCmdSet、という名前のノード追加のシンボルは、 `MRUListGroup` グループおよび `cmdidMRUList` コマンドを次のようにします。  
  
    ```c#  
    <IDSymbol name="MRUListGroup" value="0x1200"/>  
    <IDSymbol name="cmdidMRUList" value="0x0200"/>  
    ```  
  
3.  `Groups` セクションは、既存のグループのエントリに宣言されたグループを追加します。  
  
    ```cpp  
    <Group guid="guidTestCommandPackageCmdSet" id="MRUListGroup"   
           priority="0x0100">  
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenu"/>  
    </Group>  
  
    ```  
  
4.  `Buttons` セクションで、既存のボタンのエントリの後、新規に宣言されるコマンドを表すノードを追加します。  
  
    ```c#  
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
  
     `DynamicItemStart` フラグを動的に生成するコマンドを有効にします。  
  
5.  プロジェクトをビルドし、新しいコマンドの表示をテストのデバッグを開始します。  
  
     **TestMenu** \] メニューの \[新しい\] クリックして **サブメニュー**, 、新しいコマンドを表示する **MRU プレース ホルダー**します。 コマンドの動的な MRU 一覧は、次の手順では後、は、そのリストによってたびに、サブメニューが開かれているときに、このコマンドのラベルが置き換えられます。  
  
## MRU 一覧を入力  
  
1.  TestCommandPackageGuids.cs で次の行を追加、既存のコマンド Id の後に、 `TestCommandPackageGuids` クラス定義です。  
  
    ```c#  
    public const string guidTestCommandPackageCmdSet = "00000000-0000-0000-0000-00000000"; // get the GUID from the .vsct file  
    public const uint cmdidMRUList = 0x200;  
    ```  
  
2.  TestCommand.cs で次のコードを追加ステートメントを使用します。  
  
    ```c#  
    using System.Collections;  
    ```  
  
3.  AddCommand の最後の呼び出し後、TestCommand コンス トラクターで、次のコードを追加します。`InitMRUMenu` 後で定義されています。  
  
    ```c#  
    this.InitMRUMenu(commandService);  
    ```  
  
4.  TestCommand クラスでは、次のコードを追加します。 このコードでは、MRU 一覧に表示される項目を表す文字列のリストを初期化します。  
  
    ```c#  
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
  
5.  後に、 `InitializeMRUList` メソッドを追加、 `InitMRUMenu` メソッドです。 これには、MRU 一覧のメニュー コマンドを初期化します。  
  
    ```c#  
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
  
     MRU 一覧にすべての可能な項目のメニュー コマンド オブジェクトを作成する必要があります。 IDE の呼び出し、 `OnMRUQueryStatus` ない項目があるまで、MRU 一覧の各項目のメソッドです。 マネージ コードでは、ide がこれ以上項目があることを知る唯一の方法は、最初使用可能なすべての項目を作成します。 する場合は、追加、アイテムをマークで非表示としてまずを使用して `mc.Visible = false;` メニュー コマンドを作成した後です。 これらの項目、表示できる以降を使用して `mc.Visible = true;` で、 `OnMRUQueryStatus` メソッドです。  
  
6.  後に、 `InitMRUMenu` メソッドでは、次の追加 `OnMRUQueryStatus` メソッドです。 これは、ハンドラーは、最近使用した項目ごとにテキストを設定します。  
  
    ```c#  
    private void OnMRUQueryStatus(object sender, EventArgs e)  
    {  
        OleMenuCommand menuCommand = sender as OleMenuCommand;  
        if (null != menuCommand)  
        {  
            int MRUItemIndex = menuCommand.CommandID.ID - this.baseMRUID;  
            if (MRUItemIndex >= 0 && MRUItemIndex < this.mruList.Count)  
            {  
                menuCommand.Text = this.mruList[MRUItemIndex] as string;  
            }  
        }  
    }  
    ```  
  
7.  後に、 `OnMRUQueryStatus` メソッドでは、次の追加 `OnMRUExec` メソッドです。 これは、最近使用した項目を選択するためのハンドラーです。 このメソッドでは、選択した項目をリストの一番上に移動し、メッセージ ボックスに、選択したアイテムを表示します。  
  
    ```c#  
    private void OnMRUExec(object sender, EventArgs e)  
    {  
        var menuCommand = sender as OleMenuCommand;  
        if (null != menuCommand)  
        {  
            int MRUItemIndex = menuCommand.CommandID.ID - this.baseMRUID;  
            if (MRUItemIndex >= 0 && MRUItemIndex < this.mruList.Count)  
            {  
                string selection = this.mruList[MRUItemIndex] as string;  
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
  
## MRU 一覧をテスト  
  
#### 最近使用したメニューの一覧をテストするには  
  
1.  プロジェクトをビルドし、デバッグの開始  
  
2.  **TestMenu** \] メニューのをクリックして **呼び出す TestCommand**します。 これには、コマンドが選択されていることを示すメッセージ ボックスが表示されます。  
  
    > [!NOTE]
    >  読み込んで正しく MRU 一覧を表示する VSPackage を強制するには、この手順が必要です。 この手順をスキップする場合は、MRU 一覧は表示されません。  
  
3.  **テスト\] メニューの \[** \] メニューのをクリックして **サブメニュー**します。 4 つの項目の一覧は、区切り記号の下のサブメニューの最後に表示されます。 クリックすると、 **項目 3**, 、メッセージ ボックスが表示され、テキストを表示する必要があります"選択された項目 3" です。 \(4 つの項目の一覧が表示されない場合保証前の手順の指示に従って\)。  
  
4.  サブメニューをもう一度開きます。 注意して **項目 3** 一覧の上部にあるが、その他のアイテムが下の 1 つの位置に出されたとします。 をクリックして **項目 3** もう一度とメッセージ ボックスが表示される通知"選択された項目 3"、テキストがコマンド ラベルと共に新しい位置に正しく移行したことを示します。  
  
## 参照  
 [メニュー項目を動的に追加します。](../extensibility/dynamically-adding-menu-items.md)