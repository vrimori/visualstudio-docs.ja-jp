---
title: 'チュートリアル: ワークフローへのアプリケーション ページの追加 |Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
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
manager: douge
ms.workload:
- office
ms.openlocfilehash: 937fb2d5b41c2fce9fb11cc683f7abd771718e89
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/29/2018
ms.locfileid: "37119470"
---
# <a name="walkthrough-add-an-application-page-to-a-workflow"></a>チュートリアル: ワークフローへのアプリケーション ページを追加します。
  このチュートリアルでは、ワークフローから派生したワークフロー プロジェクトにデータを表示するアプリケーション ページを追加する方法を示します。 トピックで説明されているプロジェクトを基に、[チュートリアル: 関連付けと開始フォームでワークフローを作成する](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)します。  
  
 このチュートリアルでは、次のタスクについて説明します。  
  
-   SharePoint ワークフロー プロジェクトに ASPX アプリケーション ページを追加します。  
  
-   ワークフロー プロジェクトからデータを取得し、操作します。  
  
-   [アプリケーション] ページではテーブルのデータを表示しています。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>前提条件  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   サポート対象エディションの[!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)]および SharePoint。 詳細については、次を参照してください。 [SharePoint ソリューションの開発要件](../sharepoint/requirements-for-developing-sharepoint-solutions.md)します。  
  
-   Visual Studio  
  
-   トピック内のプロジェクトを完了する必要も[チュートリアル: 関連付けと開始フォームでワークフローを作成する](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)します。  
  
## <a name="ammend-the-workflow-code"></a>追記ワークフロー コード
 最初に、経費報告書の金額に結果列の値を設定するワークフローのコード行を追加します。 この値は、経費レポートの集計計算の後で使用されます。  
  
#### <a name="to-set-the-value-of-the-outcome-column-in-the-workflow"></a>ワークフローの結果列の値を設定するには
  
1.  トピックから完成したプロジェクトを読み込む[チュートリアル: 関連付けと開始フォームを持つワークフローを作成する](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)に[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]します。  
  
2.  コードを開きます*Workflow1.cs*または*Workflow1.vb* (使用するプログラミング言語) によって異なります。  
  
3.  下部に、`createTask1_MethodInvoking`メソッドを次のコードを追加します。  
  
    ```vb  
    createTask1_TaskProperties1.ExtendedProperties("Outcome") =   
      workflowProperties.InitiationData  
    ```  
  
    ```csharp  
    createTask1_TaskProperties1.ExtendedProperties["Outcome"] =   
      workflowProperties.InitiationData;  
    ```  
  
## <a name="create-an-application-page"></a>アプリケーション ページを作成します。
 次に、ASPX フォームをプロジェクトに追加します。 このフォームには、経費報告のワークフロー プロジェクトから取得したデータが表示されます。 これを行うには、アプリケーション ページを追加します。 アプリケーション ページは、SharePoint サイト上の他のページはようになります、つまり、その他の SharePoint ページとして同じマスター ページを使用します。  
  
#### <a name="to-add-an-application-page-to-the-project"></a>アプリケーション ページのプロジェクトに追加するには  
  
1.  ExpenseReport プロジェクトを選択し、次に、メニュー バーで、次のように選択します。**プロジェクト** > **新しい項目の追加**します。  
  
2.  **テンプレート**ウィンドウで、選択、**アプリケーション ページ**テンプレート、プロジェクト項目の既定の名前を使用して (**ApplicaitonPage1.aspx**)、選び、 **追加**ボタンをクリックします。  
  
3.  [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] ApplicationPage1.aspx の置換、`PlaceHolderMain`を次のセクション。  
  
    ```aspx-csharp  
    <asp:Content ID="Main" ContentPlaceHolderID="PlaceHolderMain" runat="server">  
        <asp:Label ID="Label1" runat="server" Font-Bold="True"   
            Text="Expenses that exceeded allotted amount" Font-Size="Medium"></asp:Label>  
        <br />  
        <asp:Table ID="Table1" runat="server">  
        </asp:Table>  
    </asp:Content>  
    ```  
  
     このコードでは、タイトルとページにテーブルを追加します。  
  
4.  置き換えることで、アプリケーションのページにタイトルを追加、`PlaceHolderPageTitleInTitleArea`を次のセクション。  
  
    ```aspx-csharp  
    <asp:Content ID="PageTitleInTitleArea" ContentPlaceHolderID="PlaceHolderPageTitleInTitleArea" runat="server" >  
        Expense Report Summary  
    </asp:Content>  
    ```  
  
## <a name="code-the-application-page"></a>コード アプリケーション ページ
 次に、経費明細書アプリケーションの概要ページにコードを追加します。 ページを開くと、コードは、割り当てられた使用制限を超える経費の SharePoint でのタスク一覧をスキャンします。 レポートには、経費の各項目が一覧表示します。  
  
#### <a name="to-code-the-application-page"></a>アプリケーション ページをコーディングするには  
  
1.  選択、 **ApplicationPage1.aspx**ノードで、次に、メニュー バーで、次のように選択します。**ビュー** > **コード**アプリケーション ページの背後にあるコードを表示します。  
  
2.  置換、**を使用して**または**インポート**に次のクラスの上部にある (によって、プログラミング言語) ステートメント。  
  
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
  
## <a name="test-the-application-page"></a>アプリケーション ページをテストします。
 次に、アプリケーション ページが正しく支出データを表示するかどうかを決定します。  
  
#### <a name="to-test-the-application-page"></a>アプリケーション ページをテストするには  
  
1.  選択、 **F5**キーを実行し、プロジェクトを SharePoint に配置します。  
  
2.  選択、**ホーム**ボタンをクリックし、選択し、 **Shared Documents** SharePoint サイトで共有ドキュメント の一覧を表示する quicklaunch バーのリンク。  
  
3.  この例の経費報告書を表すを選択して、ドキュメントの一覧にいくつかの新しいドキュメントをアップロードします、**ドキュメント**リンクを、**ライブラリ**、を選択し、ページの上部にあるタブ。**ドキュメントのアップロード**ツール リボンのボタンをクリックします。  
  
4.  いくつかのドキュメントをアップロードした後を選択して、ワークフローをインスタンス化、**ライブラリ**リンクを**ライブラリ**とクリックした後にページの上部にあるタブ、**ライブラリ設定**ツール リボンのボタンをクリックします。  
  
5.  **ドキュメント ライブラリ設定**ページで、選択、**ワークフロー設定**のリンクを**権限と管理**セクション。  
  
6.  **ワークフロー設定**ページで、選択、**ワークフローに追加**リンク。  
  
7.  **ワークフローに追加**ページで、選択、 **ExpenseReport - Workflow1** 、ワークフローなどのワークフローの名前を入力します**ExpenseTest**、を選択し**次**ボタンをクリックします。  
  
     ワークフロー関連付けフォームが表示されます。 これを使用して、経費の上限金額のレポートします。  
  
8.  関連付けフォームでは、次のように入力します。 **1000**に、**自動承認制限**ボックスを選び、、**関連付けるワークフロー**ボタンをクリックします。  
  
9. 選択、**ホーム**SharePoint ホーム ページに戻るボタンをクリックします。  
  
10. 選択、 **Shared Documents**クイック起動バーにリンクします。  
  
11. 下矢印を表示、それを選択し、アップロードされたドキュメントのいずれかを選択、**ワークフロー**項目。  
  
12. ワークフロー開始フォームを表示する ExpenseTest の横にあるイメージを選択します。  
  
13. **費用合計**テキスト ボックスに、1000 よりも大きい値を入力し、、**ワークフローの開始**ボタンをクリックします。  
  
     報告された経費、割り当て済みの費用の金額を超えた場合は、タスクがタスク一覧に追加されます。 という名前の列**ExpenseTest**値を持つ**完了**Shared Documents の一覧で、経費レポート アイテムにも追加されます。  
  
14. Shared Documents の一覧内の他のドキュメントの手順 11 ~ 13 を繰り返します。 (ドキュメントの正確な数重要ではありません。)  
  
15. Web ブラウザーで次の URL を開き、経費明細書アプリケーションの概要ページを表示: **http://***SystemName***/_layouts/ExpenseReport/ApplicationPage1.aspx**します。  
  
     経費レポートの概要 ページには、すべてを割り当てられている量を超えた経費報告書の値を超えている金額とすべてのレポートの合計金額が表示されます。  
  
## <a name="next-steps"></a>次の手順
 SharePoint アプリケーション ページの詳細については、次を参照してください。[用 SharePoint アプリケーション ページを作成](../sharepoint/creating-application-pages-for-sharepoint.md)です。  
  
 これらのトピックから Visual Studio で Visual Web Designer を使用して、SharePoint ページの内容を設計する方法について詳細ことができます。  
  
-   [SharePoint の web パーツを作成](../sharepoint/creating-web-parts-for-sharepoint.md)です。  
  
-   [Web パーツまたはアプリケーション ページの再利用可能なコントロール作成](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)です。  
  
## <a name="see-also"></a>関連項目
 [チュートリアル: 関連付けフォームと開始フォームとワークフローを作成します。](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)   
 [方法: アプリケーション ページを作成](../sharepoint/how-to-create-an-application-page.md)   
 [For SharePoint アプリケーション ページを作成します。](../sharepoint/creating-application-pages-for-sharepoint.md)   
 [SharePoint ソリューションを開発します。](../sharepoint/developing-sharepoint-solutions.md)  
  
