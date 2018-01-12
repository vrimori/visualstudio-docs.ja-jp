---
title: "チュートリアル: アプリケーション ページをワークフローに追加する |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, adding applications page to workflow
- application page [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 86b402e1f8b8be3adf477d67eb11387fa3091afd
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-add-an-application-page-to-a-workflow"></a>チュートリアル: ワークフローへのアプリケーション ページの追加
  このチュートリアルでは、ワークフロー プロジェクトへワークフローから派生したデータを表示するためのアプリケーション ページを追加する方法を示します。 トピックで説明されているプロジェクトを基に、[チュートリアル: アソシエーションと開始フォームを使用するワークフローを作成する](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)です。  
  
 このチュートリアルでは、次のタスクについて説明します。  
  
-   SharePoint ワークフロー プロジェクトに ASPX アプリケーション ページを追加します。  
  
-   ワークフロー プロジェクトからデータを取得し、操作します。  
  
-   [アプリケーション] ページ上のテーブルにデータを表示しています。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   サポート対象エディションの[!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)]および SharePoint。 詳細については、次を参照してください。 [SharePoint ソリューションの開発要件](../sharepoint/requirements-for-developing-sharepoint-solutions.md)です。  
  
-   Visual Studio  
  
-   このトピックで、プロジェクトを完了する必要も[チュートリアル: アソシエーションと開始フォームを使用するワークフローを作成する](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)です。  
  
## <a name="amending-the-workflow-code"></a>ワークフロー コードの修正  
 まず、経費報告書の量に結果列の値を設定するワークフローに、行のコードを追加します。 この値は、経費レポートの集計計算の後で使用されます。  
  
#### <a name="to-set-the-value-of-the-outcome-column-in-the-workflow"></a>ワークフローの結果の列の値を設定するには  
  
1.  トピックから完成したプロジェクトを読み込む[チュートリアル: アソシエーションと開始フォームを使用するワークフローを作成する](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)に[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]です。  
  
2.  Workflow1.cs または Workflow1.vb (使用するプログラミング言語) に応じて、コードを開きます。  
  
3.  下に、`createTask1_MethodInvoking`メソッド、次のコードを追加します。  
  
    ```vb  
    createTask1_TaskProperties1.ExtendedProperties("Outcome") =   
      workflowProperties.InitiationData  
    ```  
  
    ```csharp  
    createTask1_TaskProperties1.ExtendedProperties["Outcome"] =   
      workflowProperties.InitiationData;  
    ```  
  
## <a name="creating-an-application-page"></a>アプリケーション ページを作成する  
 次に、ASPX フォームをプロジェクトに追加します。 経費レポート ワークフロー プロジェクトから取得したデータは、このフォームが表示されます。 これを行うには、アプリケーション ページを追加します。 アプリケーション ページでは、SharePoint サイト上の他のページはようになります、つまり、他の SharePoint ページとして同じマスター ページを使用します。  
  
#### <a name="to-add-an-application-page-to-the-project"></a>アプリケーション ページをプロジェクトに追加するには  
  
1.  ExpenseReport プロジェクトを選択し、メニュー バーで、次のように選択します。**プロジェクト**、**新しい項目の追加**です。  
  
2.  **テンプレート** ウィンドウで、選択、**アプリケーション ページ**テンプレート プロジェクト項目の既定の名前を使用して (**ApplicaitonPage1.aspx**)、を選択し、**追加**ボタンをクリックします。  
  
3.  [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] ApplicationPage1.aspx の置換、`PlaceHolderMain`を次のセクション。  
  
    ```  
    <asp:Content ID="Main" ContentPlaceHolderID="PlaceHolderMain" runat="server">  
        <asp:Label ID="Label1" runat="server" Font-Bold="True"   
            Text="Expenses that exceeded allotted amount" Font-Size="Medium"></asp:Label>  
        <br />  
        <asp:Table ID="Table1" runat="server">  
        </asp:Table>  
    </asp:Content>  
    ```  
  
     このコードは、タイトルと共にページにテーブルを追加します。  
  
4.  置き換えることで、アプリケーションのページにタイトルを追加、`PlaceHolderPageTitleInTitleArea`を次のセクション。  
  
    ```  
    <asp:Content ID="PageTitleInTitleArea" ContentPlaceHolderID="PlaceHolderPageTitleInTitleArea" runat="server" >  
        Expense Report Summary  
    </asp:Content>  
    ```  
  
## <a name="coding-the-application-page"></a>アプリケーション ページのコーディング  
 次に、コードを経費明細書アプリケーションの概要ページに追加します。 ページを開くと、コードは、割り当てられた使用制限を超える経費の SharePoint タスク リストをスキャンします。 レポートには、各項目と共に、コストの合計が一覧表示します。  
  
#### <a name="to-code-the-application-page"></a>アプリケーション ページをコーディングするには  
  
1.  選択、 **ApplicationPage1.aspx**ノード、次に、メニュー バーで、次のように選択します。**ビュー**、**コード**アプリケーション ページで、分離コードを表示します。  
  
2.  置換、**を使用して**または**インポート**に次のクラスの上部にもよりますが、プログラミング言語) ステートメント。  
  
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
    >  必ず、"TestServer"をコードで SharePoint を実行している有効なサーバーの名前で置き換えます。  
  
## <a name="testing-the-application-page"></a>アプリケーション ページのテスト  
 次に、アプリケーション ページが正しく経費報告データを表示するかどうかを決定します。  
  
#### <a name="to-test-the-application-page"></a>アプリケーション ページをテストするには  
  
1.  実行し、プロジェクトを SharePoint に配置するには、F5 キーを選択します。  
  
2.  選択、**ホーム**ボタンをクリックしを選択し、 **Shared Documents**クイック起動バーを SharePoint サイトで共有ドキュメント の一覧を表示するリンクです。  
  
3.  この例の経費報告書を表すを選択してのドキュメント一覧にいくつか新しいドキュメントをアップロードします、**ドキュメント**リンクを、**ライブラリ**、をクリックして、ページの上部にあるタブ。**ドキュメントのアップロード**ツール リボンのボタンをクリックします。  
  
4.  一部のドキュメントをアップロードした後を選択して、ワークフローをインスタンス化、**ライブラリ**リンクを**ライブラリ**ページおよびクリックして、上部のタブ、**ライブラリ設定**ツール リボンのボタンをクリックします。  
  
5.  **ドキュメント ライブラリ設定**ページで、選択、**ワークフロー設定**内のリンク、**権限と管理**セクションです。  
  
6.  **ワークフロー設定**ページで、選択、 **、ワークフローの追加**リンクします。  
  
7.  **、ワークフローの追加**ページで、選択、 **ExpenseReport - Workflow1** 、ワークフローなど、ワークフローの名前を入力**ExpenseTest**、を選択し**次**ボタンをクリックします。  
  
     ワークフロー関連付けフォームが表示されます。 これを使用して、支出限度額をレポートします。  
  
8.  関連付けフォームに入力**1000**に、**自動承認制限**ボックスをクリックして、**関連付けるワークフロー**ボタンをクリックします。  
  
9. 選択、**ホーム**SharePoint ホーム ページに戻るにはボタンをクリックします。  
  
10. 選択、 **Shared Documents**クイック起動バー上にリンクします。  
  
11. ドロップダウン矢印を表示したり、 を選択してを選択し、アップロードしたドキュメントの 1 つを選択して、**ワークフロー**項目。  
  
12. ワークフロー開始フォームを表示する ExpenseTest の横にあるイメージを選択します。  
  
13. **経費合計**テキスト ボックスは、1000 を超える値を入力し、、**ワークフローの開始**ボタンをクリックします。  
  
     報告された経費が、割り当て済みの費用の金額を超えているときに、タスクは、タスクの一覧に追加されます。 という名前の列**ExpenseTest**値を持つ**完了**も共有ドキュメント の一覧で、経費レポート アイテムに追加されます。  
  
14. 共有ドキュメント の一覧内の他のドキュメントの手順 11 ~ 13 を繰り返します。 (ドキュメントの正確な数重要ではありません。)  
  
15. Web ブラウザーで次の URL を開くことで、経費明細書概要アプリケーション ページを表示: **http://***SystemName***/_layouts/ExpenseReport/ApplicationPage1.aspx**.  
  
     経費明細書概要ページには、すべての割り当て済みの容量を超えている支出、量を超過していたことによって、すべてのレポートの合計金額が一覧表示します。  
  
## <a name="next-steps"></a>次の手順  
 SharePoint アプリケーション ページの詳細については、次を参照してください。 [for SharePoint アプリケーション ページを作成する](../sharepoint/creating-application-pages-for-sharepoint.md)です。  
  
 複数をこれらのトピックから Visual Studio でビジュアル Web デザイナーを使用して、SharePoint ページの内容をデザインする方法について学習できます。  
  
-   [SharePoint の Web パーツの作成](../sharepoint/creating-web-parts-for-sharepoint.md)です。  
  
-   [Web パーツまたはアプリケーション ページの再利用可能なコントロールの作成](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)です。  
  
## <a name="see-also"></a>参照  
 [チュートリアル: アソシエーションと開始フォーム、ワークフローを作成します。](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)   
 [方法: アプリケーション ページを作成します。](../sharepoint/how-to-create-an-application-page.md)   
 [For SharePoint アプリケーション ページの作成](../sharepoint/creating-application-pages-for-sharepoint.md)   
 [SharePoint ソリューションの開発](../sharepoint/developing-sharepoint-solutions.md)  
  
  