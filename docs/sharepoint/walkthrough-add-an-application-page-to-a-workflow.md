---
title: "チュートリアル: ワークフローへのアプリケーション ページの追加 | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "アプリケーション ページ [Visual Studio での SharePoint 開発]"
  - "Visual Studio での SharePoint 開発, 追加 (アプリケーション ページをワークフローに)"
ms.assetid: e4845d07-917b-45cb-a569-4ecdd602fbd9
caps.latest.revision: 28
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 27
---
# チュートリアル: ワークフローへのアプリケーション ページの追加
  このチュートリアルでは、ワークフローから得られたデータを表示するためのアプリケーション ページをワークフロー プロジェクトに追加する方法について説明します。  「[チュートリアル: 関連付けフォームと開始フォームを持つワークフローの作成](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)」のトピックで取り上げたプロジェクトがベースとなります。  
  
 このチュートリアルでは、次のタスクについて説明します。  
  
-   SharePoint ワークフロー プロジェクトに ASPX アプリケーション ページを追加する。  
  
-   ワークフロー プロジェクトからデータを取得して操作する。  
  
-   アプリケーション ページ上のテーブルにデータを表示する。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## 必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   サポート対象エディションの [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] および SharePoint。  詳細については、「[SharePoint ソリューションの開発要件](../sharepoint/requirements-for-developing-sharepoint-solutions.md)」を参照してください。  
  
-   Visual Studio  
  
-   さらに、「[チュートリアル: 関連付けフォームと開始フォームを持つワークフローの作成](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)」のトピックで作成したプロジェクトが必要です。  
  
## ワークフロー コードの修正  
 まず、Outcome 列の値を経費明細書の金額に設定するコード行をワークフローに追加します。  この値は、後で経費明細書の概要 \(Expense Report Summary\) の計算に使用します。  
  
#### ワークフローで Outcome 列の値を設定するには  
  
1.  「[チュートリアル: 関連付けフォームと開始フォームを持つワークフローの作成](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)」で作成したプロジェクトを [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] に読み込みます。  
  
2.  プログラミング言語に応じて Workflow1.cs または Workflow1.vb のコードを開きます。  
  
3.  `createTask1_MethodInvoking` メソッドの最後に、次のコードを追加します。  
  
    ```vb  
    createTask1_TaskProperties1.ExtendedProperties("Outcome") =   
      workflowProperties.InitiationData  
    ```  
  
    ```csharp  
    createTask1_TaskProperties1.ExtendedProperties["Outcome"] =   
      workflowProperties.InitiationData;  
    ```  
  
## アプリケーション ページを作成する  
 次に、ASPX フォームをプロジェクトに追加します。  このフォームには、経費明細書ワークフロー プロジェクトから取得されたデータを表示します。  ここでは、そのためのアプリケーション ページを追加します。  アプリケーション ページには、他の SharePoint ページと同じマスター ページを使用します。つまり、外見上は SharePoint サイトの他のページと似ています。  
  
#### プロジェクトにアプリケーション ページを追加するには  
  
1.  次に、ExpenseReport のプロジェクトを選択し、メニュー バーで選択し、**\[新しいアイテムの追加\]\[プロジェクト\]** をクリックします。  
  
2.  **\[テンプレート\]** のペインで、**\[アプリケーション ページ\]** のテンプレートを使用し、既定の名前をプロジェクト項目 \(**ApplicaitonPage1.aspx**\) の場合は、選択します **\[追加\]** ボタンをクリックします。  
  
3.  ApplicationPage1.aspx の [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] で、`PlaceHolderMain` セクションを次の内容に置き換えます。  
  
    ```  
    <asp:Content ID="Main" ContentPlaceHolderID="PlaceHolderMain" runat="server">  
        <asp:Label ID="Label1" runat="server" Font-Bold="True"   
            Text="Expenses that exceeded allotted amount" Font-Size="Medium"></asp:Label>  
        <br />  
        <asp:Table ID="Table1" runat="server">  
        </asp:Table>  
    </asp:Content>  
    ```  
  
     このコードによって、ページにテーブルとタイトルが追加されます。  
  
4.  `PlaceHolderPageTitleInTitleArea` セクションを次のように置き換えて、アプリケーション ページにタイトルを追加します。  
  
    ```  
    <asp:Content ID="PageTitleInTitleArea" ContentPlaceHolderID="PlaceHolderPageTitleInTitleArea" runat="server" >  
        Expense Report Summary  
    </asp:Content>  
    ```  
  
## アプリケーション ページのコーディング  
 次に、経費明細書の概要を表示するアプリケーション ページにコードを追加します。  ページを開くと、SharePoint 内のタスク リストがスキャンされ、割り当てられた支出制限を超える経費がないかどうかが調べられます。  経費明細書には、個々の項目と経費の合計が一覧表示されます。  
  
#### アプリケーション ページをコーディングするには  
  
1.  次に **\[ApplicationPage1.aspx\]** ノードを選択し、メニュー バーをクリックして、アプリケーション ページの分離コードを表示するには、**\[コード\]\[表示\]** をクリックします。  
  
2.  プログラミング言語に応じて、クラスの冒頭の **using** ステートメントまたは **Import** ステートメントを次のように置き換えます。  
  
    ```vb  
    Imports System  
    Imports Microsoft.SharePoint  
    Imports Microsoft.SharePoint.WebControls  
    Imports System.Collections  
    Imports System.Data  
    Imports System.Web.UI  
    Imports System.Web.UI.WebControls  
    Imports System.Web.UI.WebControls.WebParts  
    Imports System.Drawing  
    Imports Microsoft.SharePoint.Navigation  
    ```  
  
    ```csharp  
    using System;  
    using Microsoft.SharePoint;  
    using Microsoft.SharePoint.WebControls;  
    using System.Collections;  
    using System.Data;  
    using System.Web.UI;  
    using System.Web.UI.WebControls;  
    using System.Web.UI.WebControls.WebParts;  
    using System.Drawing;  
    using Microsoft.SharePoint.Navigation;  
    ```  
  
3.  `Page_Load` メソッドに次のコードを追加します。  
  
    ```vb  
    Try  
        ' Reference the Tasks list on the SharePoint site.  
        ' Replace "TestServer" with a valid SharePoint server name.  
        Dim site As SPSite = New SPSite("http://TestServer")  
        Dim list As SPList = site.AllWebs(0).Lists("Tasks")  
        ' string text = "";  
        Dim sum As Integer = 0  
        Table1.Rows.Clear()  
        ' Add table headers.  
        Dim hr As TableHeaderRow = New TableHeaderRow  
        hr.BackColor = Color.LightBlue  
        Dim hc1 As TableHeaderCell = New TableHeaderCell  
        Dim hc2 As TableHeaderCell = New TableHeaderCell  
        hc1.Text = "Expense Report Name"  
        hc2.Text = "Amount Exceeded"  
        hr.Cells.Add(hc1)  
        hr.Cells.Add(hc2)  
        ' Add the TableHeaderRow as the first item   
        ' in the Rows collection of the table.  
        Table1.Rows.AddAt(0, hr)  
        ' Iterate through the tasks in the Task list and collect those    
        ' that have values in the "Related Content" and "Outcome" fields   
        ' - the fields written to when expense approval is required.  
        For Each item As SPListItem In list.Items  
            Dim s_relContent As String = ""  
            Dim s_outcome As String = ""  
            Try  
                ' Task has the fields - treat as expense report.  
                s_relContent = item.GetFormattedValue("Related Content")  
                s_outcome = item.GetFormattedValue("Outcome")  
            Catch erx As System.Exception  
                ' Task does not have fields - skip it.  
                Continue For  
            End Try  
            ' Convert amount to an int and keep a running total.  
            If (Not String.IsNullOrEmpty(s_relContent) And Not   
              String.IsNullOrEmpty(s_outcome)) Then  
                sum = (sum + Convert.ToInt32(s_outcome))  
                Dim relContent As TableCell = New TableCell  
                relContent.Text = s_relContent  
                Dim outcome As TableCell = New TableCell  
                outcome.Text = ("$" + s_outcome)  
                Dim dataRow2 As TableRow = New TableRow  
                dataRow2.Cells.Add(relContent)  
                dataRow2.Cells.Add(outcome)  
                Table1.Rows.Add(dataRow2)  
            End If  
        Next  
        ' Report the sum of the reports in the table footer.  
        Dim tfr As TableFooterRow = New TableFooterRow  
        tfr.BackColor = Color.LightGreen  
        ' Create a TableCell object to contain the   
        ' text for the footer.  
        Dim ftc1 As TableCell = New TableCell  
        Dim ftc2 As TableCell = New TableCell  
        ftc1.Text = "TOTAL: "  
        ftc2.Text = ("$" + Convert.ToString(sum))  
        ' Add the TableCell object to the Cells  
        ' collection of the TableFooterRow.  
        tfr.Cells.Add(ftc1)  
        tfr.Cells.Add(ftc2)  
        ' Add the TableFooterRow to the Rows  
        ' collection of the table.  
        Table1.Rows.Add(tfr)  
    Catch errx As Exception  
        System.Diagnostics.Debug.WriteLine(("Error: " + errx.ToString))  
    End Try  
    ```  
  
    ```csharp  
    try  
    {  
        // Reference the Tasks list on the SharePoint site.  
        // Replace "TestServer" with a valid SharePoint server name.  
        SPSite site = new SPSite("http://TestServer");  
        SPList list = site.AllWebs[0].Lists["Tasks"];  
  
        // string text = "";  
        int sum = 0;  
  
        Table1.Rows.Clear();  
  
        // Add table headers.  
        TableHeaderRow hr = new TableHeaderRow();  
        hr.BackColor = Color.LightBlue;  
        TableHeaderCell hc1 = new TableHeaderCell();  
        TableHeaderCell hc2 = new TableHeaderCell();  
        hc1.Text = "Expense Report Name";  
        hc2.Text = "Amount Exceeded";  
        hr.Cells.Add(hc1);  
        hr.Cells.Add(hc2);  
        // Add the TableHeaderRow as the first item   
        // in the Rows collection of the table.  
        Table1.Rows.AddAt(0, hr);  
  
        // Iterate through the tasks in the Task list and collect those   
        // that have values in the "Related Content" and "Outcome"   
        // fields - the fields written to when expense approval is   
        // required.  
        foreach (SPListItem item in list.Items)  
        {  
            string s_relContent = "";  
            string s_outcome = "";  
  
            try  
            {  
                // Task has the fields - treat as expense report.  
                s_relContent = item.GetFormattedValue("Related   
                  Content");  
                s_outcome = item.GetFormattedValue("Outcome");  
            }  
            catch  
            {  
                // Task does not have fields - skip it.  
                continue;  
            }  
  
            if (!String.IsNullOrEmpty(s_relContent) &&   
              !String.IsNullOrEmpty(s_outcome))  
            {  
                // Convert amount to an int and keep a running total.  
                sum += Convert.ToInt32(s_outcome);  
                TableCell relContent = new TableCell();  
                relContent.Text = s_relContent;  
                TableCell outcome = new TableCell();  
                outcome.Text = "$" + s_outcome;  
                TableRow dataRow2 = new TableRow();  
                dataRow2.Cells.Add(relContent);  
                dataRow2.Cells.Add(outcome);  
                Table1.Rows.Add(dataRow2);  
            }  
        }  
  
        // Report the sum of the reports in the table footer.  
           TableFooterRow tfr = new TableFooterRow();  
        tfr.BackColor = Color.LightGreen;  
  
        // Create a TableCell object to contain the   
        // text for the footer.  
        TableCell ftc1 = new TableCell();  
        TableCell ftc2 = new TableCell();  
        ftc1.Text = "TOTAL: ";  
        ftc2.Text = "$" + Convert.ToString(sum);  
  
        // Add the TableCell object to the Cells  
        // collection of the TableFooterRow.  
        tfr.Cells.Add(ftc1);  
        tfr.Cells.Add(ftc2);  
  
        // Add the TableFooterRow to the Rows  
        // collection of the table.  
        Table1.Rows.Add(tfr);  
    }  
  
    catch (Exception errx)  
    {  
        System.Diagnostics.Debug.WriteLine("Error: " + errx.ToString());  
    }  
    ```  
  
    > [!WARNING]  
    >  SharePoint を実行しているサーバーの有効な名前とコードの「TestServer」を使用してください。  
  
## アプリケーション ページのテスト  
 次に、アプリケーション ページに経費データが正しく表示されるかどうかを確認します。  
  
#### アプリケーション ページをテストするには  
  
1.  SharePoint にプロジェクトを実行するには、F5 キーを押します。  
  
2.  **\[ホーム\]** ボタンをクリックし、共有ドキュメントを表示するには、クイック起動バーの **\[共有ドキュメント\]** リンクが SharePoint サイトを選択します。  
  
3.  この例の経費明細書を表すには、ドキュメント リストに新しいドキュメントをページの先頭に **\[LibraryTools\]** タブの **\[ドキュメント\]** リンクをクリックし、ツール リボンの **\[ドキュメントのアップロード\]** ボタンをクリックしてアップロードします。  
  
4.  いくつかのドキュメントをアップロードしたら、ページの上部に **\[LibraryTools\]** タブの **\[ライブラリ\]** リンクをクリックし、ツール リボンの **\[ライブラリの設定\]** ボタンをクリックして、ワークフローをインスタンス化してください。  
  
5.  **\[ドキュメント ライブラリの設定\]** ページで、**\[権限と管理\]** セクションの **\[ワークフロー設定\]** リンクをクリックします。  
  
6.  **\[ワークフロー設定\]** ページで、**\[ワークフローの追加\]** リンクをクリックします。  
  
7.  **\[ワークフローの追加\]** ページで、**\[ExpenseReport \- Workflow1\]** のワークフローを選択し、ワークフローの名前を" ExpenseTest "など\) を入力し、**\[次へ\]** ボタンをクリックします。  
  
     ワークフローの関連付けフォームが表示されます。  ここで経費の上限金額を記録します。  
  
8.  関連付けフォームで、**1000** を **\[Auto Approval Limit\]** ボックスに入力し、**\[ワークフローの関連付け\]** ボタンをクリックします。  
  
9. SharePoint のホーム ページに戻るに **\[ホーム\]** ボタンをクリックします。  
  
10. クイック起動バーの **\[共有ドキュメント\]** リンクをクリックします。  
  
11. ドロップダウン矢印が表示用にアップロードするドキュメントの 1 をクリックして、ファイルを選択し、**\[ワークフロー\]** 項目を選択します。  
  
12. ワークフローの開始フォームを表示するには、ExpenseTest の横に表示されるイメージをクリックします。  
  
13. **\[経費の合計\]** のテキスト ボックスに、1000 より大きい入力し、**\[ワークフローの開始\]** ボタンを選択し、値を生成します。  
  
     報告された経費が、割り当てられている経費金額を超えると、タスク リストにタスクが追加されます。  また、共有ドキュメント リストの経費明細書項目に、**ExpenseTest** という列が追加され、列の値は **\[完了\]** となります。  
  
14. 共有ドキュメント リスト内の他のドキュメントについても手順 11. ～ 13. を繰り返します。ドキュメントの正確な数は重要ではありません。  
  
15. Web ブラウザーに次の URL を開き、経費明細書の概要のアプリケーション ページを表示する: **http:\/\/***SystemName***\/\_layouts\/ExpenseReport\/ApplicationPage1.aspx**。  
  
     このページには、割り当て金額を超えたすべての経費明細書と超過金額、およびすべての経費明細書の合計金額が表示されます。  
  
## 次の手順  
 SharePoint のアプリケーション ページの詳細については、「[SharePoint のアプリケーション ページの作成](../sharepoint/creating-application-pages-for-sharepoint.md)」を参照してください。  
  
 Visual Studio の Visual Web Designer を使用して、SharePoint ページの内容をデザインする方法の詳細については、以下のトピックを参照してください。  
  
-   [SharePoint の Web パーツの作成](../sharepoint/creating-web-parts-for-sharepoint.md).  
  
-   [Web パーツまたはアプリケーション ページの再利用できるコントロールの作成](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md).  
  
## 参照  
 [チュートリアル: 関連付けフォームと開始フォームを持つワークフローの作成](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)   
 [方法: アプリケーション ページを作成する](../sharepoint/how-to-create-an-application-page.md)   
 [SharePoint のアプリケーション ページの作成](../sharepoint/creating-application-pages-for-sharepoint.md)   
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)  
  
  