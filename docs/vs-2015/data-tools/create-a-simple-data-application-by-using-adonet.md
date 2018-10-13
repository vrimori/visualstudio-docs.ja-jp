---
title: ADO.NET を使用して単純なデータ アプリケーションの作成 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
ms.assetid: 2222841f-e443-4a3d-8c70-4506aa905193
caps.latest.revision: 46
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7a38d92aa43056b3824b4d583ccd93f255b1439f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49204310"
---
# <a name="create-a-simple-data-application-by-using-adonet"></a>ADO.NET を使用して単純なデータ アプリケーションを作成します。
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
データベースのデータを処理するアプリケーションの作成では、接続文字列の定義、データの挿入、ストアド プロシージャの実行などの基本的なタスクを実行します。 このトピックでは、Visual c# または Visual Basic および ADO.NET を使用して単純な Windows フォームの「フォーム オーバー データ」アプリケーションからデータベースと対話する方法を検出できます。  すべての .NET データ テクノロジ: LINQ to SQL、および Entity Framework のデータセットを含む-最終的にこの記事で示したものとよく似ている手順を実行します。  
  
 この記事では、非常に高速の方法で、データベースからデータを取得する簡単な方法を示します。 を、アプリケーションが自明でない方法でデータを変更し、データベースを更新する必要がある場合は、Entity Framework を使用して、基になるデータの変更をユーザー インターフェイス コントロールを自動的に同期へのデータ バインディングを使用してを検討してください。  
  
> [!IMPORTANT]
>  コードをシンプルにするため、運用環境で使用する例外処理は含まれていません。  
  
 **このトピックの内容**  
  
-   [サンプル データベースを設定します。](../data-tools/create-a-simple-data-application-by-using-adonet.md#BKMK_setupthesampledatabase)  
  
-   [フォームを作成して、コントロールを追加します。](../data-tools/create-a-simple-data-application-by-using-adonet.md#BKMK_createtheformsandaddcontrols)  
  
-   [接続文字列を保存します。](../data-tools/create-a-simple-data-application-by-using-adonet.md#BKMK_storetheconnectionstring)  
  
-   [接続文字列を取得します。](../data-tools/create-a-simple-data-application-by-using-adonet.md#BKMK_retrievetheconnectionstring)  
  
-   [フォームのコードを記述します。](../data-tools/create-a-simple-data-application-by-using-adonet.md#BKMK_writethecodefortheforms)  
  
-   [アプリケーションをテストします。](../data-tools/create-a-simple-data-application-by-using-adonet.md#BKMK_testyourapplication)  
  
## <a name="prerequisites"></a>必須コンポーネント  
 アプリケーションの作成には、次が必要です:  
  
-   Visual Studio Community エディション。  
  
-   SQL Server Express LocalDB です。  
  
-   次の手順で作成したサンプルの小さなデータベース[スクリプトを使用して SQL database を作成する](../data-tools/create-a-sql-database-by-using-a-script.md)します。  
  
-   設定が完了したデータベースへの接続文字列。 開いてこの値を調べる**SQL Server オブジェクト エクスプ ローラー**、データベースのショートカット メニューを開き、選択**プロパティ**にスクロールし、 **ConnectionString**プロパティ。  
  
 このトピックは、Visual Studio IDE の基本的な機能を理解していて、Windows フォーム アプリケーションの作成、そのプロジェクトへのフォームの追加、フォームにボタンなどのコントロールの追加、コントロールのプロパティの設定、およびシンプルなイベントのコード記述ができることを前提としています。 完了することをお勧め、これらのタスクを慣れていない場合、 [Visual c# および Visual Basic の概要](../ide/getting-started-with-visual-csharp-and-visual-basic.md)このトピックを開始する前にします。  
  
##  <a name="BKMK_setupthesampledatabase"></a> サンプル データベースを設定します。  
 このチュートリアルで扱うサンプル データベースには、「Customer (顧客)」と「Order (注文)」のテーブルがあります。 最初はテーブルにデータはありませんが、作成したアプリケーションを実行するとデータが追加されます。 データベースには、5 種類のシンプルなストアド プロシージャもあります。 [スクリプトを使用して SQL database を作成する](../data-tools/create-a-sql-database-by-using-a-script.md)テーブル、主キーと外部キー、制約、およびストアド プロシージャを作成する TRANSACT-SQL スクリプトが含まれています。  
  
##  <a name="BKMK_createtheformsandaddcontrols"></a> フォームを作成して、コントロールを追加します。  
  
1.  Windows フォーム アプリケーションでは、プロジェクトを作成し、SimpleDataApp と名前をつけます。  
  
     Visual Studio は、Form1 という名前の空の Windows フォームを含めた、いくつかのファイルとプロジェクトを作成します。  
  
2.  3 つの形式を持つように、2 つの Windows フォームをプロジェクトに追加し、次の名前を付けるし。  
  
    -   ナビゲーション  
  
    -   NewCustomer  
  
    -   FillOrCancel  
  
3.  各フォームに、次の図に示されるように、テキスト ボックス、ボタン、および他のコントロールを追加します。 各コントロールに、テーブルを示すプロパティを設定します。  
  
    > [!NOTE]
    >  グループ ボックス、およびラベル コントロールは明確性を追加しますが、コードでは使用されません。  
  
 **Navigation フォーム**  
  
 ![ダイアログ ボックスのナビゲーション](../data-tools/media/simpleappnav.png "SimpleAppNav")  
  
|Navigation フォームのコントロール|プロパティ|  
|--------------------------------------|----------------|  
|ボタン|Name = btnGoToAdd|  
|ボタン|Name = btnGoToFillOrCancel|  
|ボタン|Name = btnExit|  
  
 **NewCustomer フォーム**  
  
 ![新しい顧客を追加し、注文](../data-tools/media/simpleappnewcust.png "SimpleAppNewCust")  
  
|NewCustomer フォームのコントロール|プロパティ|  
|---------------------------------------|----------------|  
|TextBox|Name = txtCustomerName|  
|TextBox|Name = txtCustomerID<br /><br /> Readonly = True|  
|ボタン|Name = btnCreateAccount|  
|NumericUpdown|DecimalPlaces = 0<br /><br /> Maximum = 5000<br /><br /> Name = numOrderAmount|  
|DateTimePicker|Format = Short<br /><br /> Name = dtpOrderDate|  
|ボタン|Name = btnPlaceOrder|  
|ボタン|Name = btnAddAnotherAccount|  
|ボタン|Name = btnAddFinish|  
  
 **FillOrCancel フォーム**  
  
 ![入力するか、または注文をキャンセル](../data-tools/media/simpleappcancelfill.png "SimpleAppCancelFill")  
  
|FillOrCancel フォームのコントロール|プロパティ|  
|----------------------------------------|----------------|  
|TextBox|Name = txtOrderID|  
|ボタン|Name = btnFindByOrderID|  
|DateTimePicker|Format = Short<br /><br /> Name = dtpFillDate|  
|DataGridView|Name = dgvCustomerOrders<br /><br /> Readonly = True<br /><br /> RowHeadersVisible = False|  
|ボタン|Name = btnCancelOrder|  
|ボタン|Name = btnFillOrder|  
|ボタン|Name = btnFinishUpdates|  
  
##  <a name="BKMK_storetheconnectionstring"></a> 接続文字列を保存します。  
 アプリケーションがデータベースの接続を開くとき、アプリケーションは接続文字列にアクセスする必要があります。 各フォーム上の文字列を手動で入力しなくても、プロジェクトで、アプリケーション構成ファイルに文字列を格納し、メソッドは、アプリケーションのすべてのフォームから呼び出されたときに、文字列を返すメソッドを作成します。  
  
 内の接続文字列を検索する**SQL Server オブジェクト エクスプ ローラー**でデータベースを右クリックし、選択**プロパティ**、ConnectionString プロパティを検索します。 Ctrl キーを押しながら A キーを使用すると、文字列を選択します。  
  
1.  **ソリューション エクスプ ローラー**を選択、**プロパティ**ノードをクリックして、プロジェクトの下で**Settings.settings**します。  
  
2.  **名前**列、入力`connString`します。  
  
3.  **型**一覧で、 **(接続文字列)** します。  
  
4.  **スコープ**一覧で、**アプリケーション**します。  
  
5.  **値**列で、(任意の外部の引用符)、なし、接続文字列を入力し、変更を保存します。  
  
> [!NOTE]
>  実際のアプリケーションでは文字列を格納する接続」の説明に従って、安全に[接続文字列と構成ファイル](http://msdn.microsoft.com/library/37df2641-661e-407a-a3fb-7bf9540f01e8)します。  
  
##  <a name="BKMK_retrievetheconnectionstring"></a> 接続文字列を取得します。  
  
1.  メニュー バーで選択**プロジェクト** > **参照の追加**、し、System.Configuration.dll への参照を追加します。  
  
2.  メニュー バーで選択**プロジェクト** > **クラスの追加**クラス ファイルをプロジェクトに追加し、ファイルの名前を`Utility`します。  
  
     Visual Studio がファイルを作成し、表示で**ソリューション エクスプ ローラー**します。  
  
3.  Utility ファイルでプレースホルダー コードを次のコードに置き換えます。 コードのセクションを識別する (Util- が付けられた) 番号付きのコメントを確認します。 テーブルはコードに従ってキー ポイントを呼び出します。  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.Linq;  
    using System.Text;  
    using System.Threading.Tasks;  
    //Util-1 More namespaces.  
    using System.Configuration;   
  
    namespace SimpleDataApp  
    {  
        internal class Utility  
        {  
  
            //Get the connection string from App config file.  
            internal static string GetConnectionString()  
            {  
                //Util-2 Assume failure.  
                string returnValue = null;  
  
                //Util-3 Look for the name in the connectionStrings section.  
                ConnectionStringSettings settings =  
                ConfigurationManager.ConnectionStrings["SimpleDataApp.Properties.Settings.connString"];  
  
                //If found, return the connection string.  
                if (settings != null)  
                    returnValue = settings.ConnectionString;  
  
                return returnValue;  
            }  
        }  
    }  
    ```  
  
    ```vb  
    Imports System  
    Imports System.Collections.Generic  
    Imports System.Linq  
    Imports System.Text  
    Imports System.Threading.Tasks  
    ' Util-1 More namespaces.  
    Imports System.Configuration  
  
    Namespace SimpleDataApp  
        Friend Class Utility  
  
            ' Get connection string from App config file.  
            Friend Shared Function GetConnectionString() As String  
  
                ' Util-2 Assume failure.  
                Dim returnValue As String = Nothing  
  
                ' Util-3 Look for the name in the connectionStrings section.  
                Dim settings As ConnectionStringSettings = ConfigurationManager.ConnectionStrings("SimpleDataApp.My.MySettings.connString")  
  
                ' If found, return the connection string.  
                If settings IsNot Nothing Then  
                    returnValue = settings.ConnectionString  
                End If  
  
                Return returnValue  
            End Function  
        End Class  
    End Namespace  
    ```  
  
    |コメント|説明|  
    |-------------|-----------------|  
    |Util-1|`System.Configuration` 名前空間を追加します。|  
    |Util-2|変数 `returnValue` を定義し、`null` (C#)、または `Nothing` (Visual Basic) に初期化します。|  
    |Util-3|入力した場合でも`connString`内の接続文字列の名前として、**プロパティ**指定する必要があります ウィンドウ、 `"SimpleDataApp.Properties.Settings.connString"` (c#) または`"SimpleDataApp.My.MySettings.connString"`(Visual Basic)、コードでします。|  
  
##  <a name="BKMK_writethecodefortheforms"></a> フォームのコードを記述します。  
 このセクションには、各フォームの動作を簡単な概要と、フォームを作成するコードがあります。 番号付きコメントは、コードのセクションを識別します。  
  
### <a name="navigation-form"></a>Navigation フォーム  
 Navigation フォームはアプリケーションを実行すると開きます。 **アカウントを追加**NewCustomer フォームを開きます。 **Fill またはキャンセル オーダー** FillOrCancel フォームを開きます。 **終了**ボタンは、アプリケーションを閉じます。  
  
#### <a name="make-the-navigation-form-the-startup-form"></a>Navigation フォームをスタートアップ フォームに設定  
 C# を使用している場合**ソリューション エクスプ ローラー**Program.cs を開き、変更、`Application.Run`この行。 `Application.Run(new Navigation());`  
  
 Visual Basic の場合に使用する場合**ソリューション エクスプ ローラー**、オープン、**プロパティ**ウィンドウで、**アプリケーション**、タブを選び**SimpleDataApp.Navigation**で、**スタートアップ フォーム**一覧。  
  
#### <a name="create-event-handlers"></a>イベント ハンドラーを作成する  
 空のイベント ハンドラー メソッドを作成するフォーム上の 3 つのボタンをダブルクリックします。  
  
#### <a name="create-code-for-navigation"></a>Navigation のコードを作成する  
 Navigation フォームで、既存のコードを次のコードに書き換えます。  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.ComponentModel;  
using System.Data;  
using System.Drawing;  
using System.Linq;  
using System.Text;  
using System.Threading.Tasks;  
using System.Windows.Forms;  
  
namespace SimpleDataApp  
{  
    public partial class Navigation : Form  
    {  
        public Navigation()  
        {  
            InitializeComponent();  
        }  
  
        //Open the NewCustomer form as a dialog box, which will return focus to the calling form when it closes.  
        private void btnGoToAdd_Click(object sender, EventArgs e)  
        {  
            Form frm = new NewCustomer();  
            frm.Show();  
        }  
  
        //Open the FillorCancel form as a dialog box.  
        private void btnGoToFillOrCancel_Click(object sender, EventArgs e)  
        {  
            Form frm = new FillOrCancel();  
            frm.ShowDialog();  
        }  
  
        //Close the application, not just the Navigation form.  
        private void btnExit_Click(object sender, EventArgs e)  
        {  
            this.Close();  
        }  
    }  
}  
```  
  
```vb  
Imports System  
Imports System.Collections.Generic  
Imports System.ComponentModel  
Imports System.Data  
Imports System.Drawing  
Imports System.Linq  
Imports System.Text  
Imports System.Threading.Tasks  
Imports System.Windows.Forms  
  
Namespace SimpleDataApp  
    Partial Public Class Navigation  
        Inherits Form  
        Public Sub New()  
            InitializeComponent()  
        End Sub  
  
        ' Open the NewCustomer form as a dialog box, which will return focus to the calling form when it closes.  
        Private Sub btnGoToAdd_Click() Handles btnGoToAdd.Click  
            Dim frm As Form = New NewCustomer()  
            frm.Show()  
        End Sub  
  
        ' Open the FillorCancel form as a dialog box.  
        Private Sub btnGoToFillOrCancel_Click() Handles btnGoToFillOrCancel.Click  
            Dim frm As Form = New FillOrCancel()  
            frm.ShowDialog()  
        End Sub  
  
        ' Close the application, not just the Navigation form.  
        Private Sub btnExit_Click() Handles btnExit.Click  
            Me.Close()  
        End Sub  
    End Class  
End Namespace  
  
```  
  
### <a name="newcustomer-form"></a>NewCustomer フォーム  
 顧客名を入力しを選択し、**アカウントの作成**ボタン、NewCustomer フォームは、お客様のアカウントを作成し、SQL Server は、新しいアカウント番号として IDENTITY 値を返します。 金額と注文日を指定して選択、し、新しいアカウントの注文を配置する、 **Place Order**ボタンをクリックします。  
  
#### <a name="create-event-handlers"></a>イベント ハンドラーを作成する  
 フォームの各ボタン空のクリック イベント ハンドラーを作成します。  
  
#### <a name="create-code-for-newcustomer"></a>NewCustomer のコードを作成する  
 NewCustomer フォームに次のコードを追加します。 番号付きコメントおよびコードに続くテーブルを使用して、各コード ブロックをステップ実行します。  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.ComponentModel;  
using System.Data;  
using System.Drawing;  
using System.Linq;  
using System.Text;  
using System.Threading.Tasks;  
using System.Windows.Forms;  
//NC-1 More namespaces.  
using System.Data.SqlClient;  
using System.Configuration;  
  
namespace SimpleDataApp  
{  
    public partial class NewCustomer : Form  
    {  
        //NC-2 Storage for IDENTITY values returned from database.  
        private int parsedCustomerID;  
        private int orderID;  
  
        //NC-3 Specify a connection string.  
        string connstr = SimpleDataApp.Utility.GetConnectionString();  
  
        public NewCustomer()  
        {  
            InitializeComponent();  
        }  
  
        //NC-4 Create account.  
        private void btnCreateAccount_Click(object sender, EventArgs e)  
        {  
            //NC-5 Set up and run stored procedure only if Customer Name is present.  
            if (isCustomerName())  
            {  
  
                //NC-6 Create the connection.  
                SqlConnection conn = new SqlConnection(connstr);  
  
                //NC-7 Create a SqlCommand, and identify it as a stored procedure.  
                SqlCommand cmdNewCustomer = new SqlCommand("Sales.uspNewCustomer", conn);  
                cmdNewCustomer.CommandType = CommandType.StoredProcedure;  
  
                //NC-8 Add input parameter from the stored procedure and specify what to use as its value.  
                cmdNewCustomer.Parameters.Add(new SqlParameter("@CustomerName", SqlDbType.NVarChar, 40));  
                cmdNewCustomer.Parameters["@CustomerName"].Value = txtCustomerName.Text;  
  
                //NC-9 Add output parameter.  
                cmdNewCustomer.Parameters.Add(new SqlParameter("@CustomerID", SqlDbType.Int));  
                cmdNewCustomer.Parameters["@CustomerID"].Direction = ParameterDirection.Output;  
  
                //NC-10 try-catch-finally  
                try  
                {  
                    //NC-11 Open the connection.  
                    conn.Open();  
  
                    //NC-12 Run the stored procedure.  
                    cmdNewCustomer.ExecuteNonQuery();  
  
                    //NC-13 Customer ID is an IDENTITY value from the database.   
                    this.parsedCustomerID = (int)cmdNewCustomer.Parameters["@CustomerID"].Value;  
                    this.txtCustomerID.Text = Convert.ToString(parsedCustomerID);  
  
                }  
                catch  
                {  
                    //NC-14 A simple catch.  
  
                    MessageBox.Show("Customer ID was not returned. Account could not be created.");  
                }  
                finally  
                {  
                    //NC-15 Close the connection.  
                    conn.Close();  
                }  
            }  
        }  
  
        //NC-16 Verify that Customer Name is present.  
        private bool isCustomerName()  
        {  
            if (txtCustomerName.Text == "")  
            {  
                MessageBox.Show("Please enter a name.");  
                return false;  
            }  
            else  
            {  
                return true;  
            }  
        }  
  
        //NC-17 Place order.  
        private void btnPlaceOrder_Click(object sender, EventArgs e)  
        {  
            //NC-18 Set up and run stored procedure only if required input is present.  
            if (isPlaceOrderReady())  
            {  
                // Create the connection.  
                SqlConnection conn = new SqlConnection(connstr);  
  
                //NC-19 Create SqlCommand and identify it as a stored procedure.  
                SqlCommand cmdNewOrder = new SqlCommand("Sales.uspPlaceNewOrder", conn);  
                cmdNewOrder.CommandType = CommandType.StoredProcedure;  
  
                //NC-20 @CustomerID, which was an output parameter from uspNewCustomer.  
                cmdNewOrder.Parameters.Add(new SqlParameter("@CustomerID", SqlDbType.Int));  
                cmdNewOrder.Parameters["@CustomerID"].Value = this.parsedCustomerID;  
  
                //NC-21 @OrderDate.  
                cmdNewOrder.Parameters.Add(new SqlParameter("@OrderDate", SqlDbType.DateTime, 8));  
                cmdNewOrder.Parameters["@OrderDate"].Value = dtpOrderDate.Value;  
  
                //NC-22 @Amount.  
                cmdNewOrder.Parameters.Add(new SqlParameter("@Amount", SqlDbType.Int));  
                cmdNewOrder.Parameters["@Amount"].Value = numOrderAmount.Value;  
  
                //NC-23 @Status. For a new order, the status is always O (open).  
                cmdNewOrder.Parameters.Add(new SqlParameter("@Status", SqlDbType.Char, 1));  
                cmdNewOrder.Parameters["@Status"].Value = "O";  
  
                //NC-24 Add return value for stored procedure, which is orderID.  
                cmdNewOrder.Parameters.Add(new SqlParameter("@RC", SqlDbType.Int));  
                cmdNewOrder.Parameters["@RC"].Direction = ParameterDirection.ReturnValue;  
  
                //try-catch-finally  
                try  
                {  
                    //Open connection.  
                    conn.Open();  
  
                    //Run the stored procedure.  
                    cmdNewOrder.ExecuteNonQuery();  
  
                    //NC-25 Display the order number.  
                    this.orderID = (int)cmdNewOrder.Parameters["@RC"].Value;  
                    MessageBox.Show("Order number " + this.orderID + " has been submitted.");  
                }  
                catch  
                {  
                    //A simple catch.  
                    MessageBox.Show("Order could not be placed.");  
                }  
                finally  
                {  
                    //Close connection.  
                    conn.Close();  
                }  
            }  
        }  
  
        //NC-26 Verify that order data is ready.  
        private bool isPlaceOrderReady()  
        {  
            // Verify that CustomerID is present.  
            if (txtCustomerID.Text == "")  
            {  
                MessageBox.Show("Please create customer account before placing order.");  
                return false;  
            }  
  
            // Verify that Amount isn't 0.   
            else if ((numOrderAmount.Value < 1))  
            {  
                MessageBox.Show("Please specify an order amount.");  
                return false;  
            }  
            else  
            {  
                // Order can be submitted.  
                return true;  
            }  
        }  
  
        //NC-27 Reset the form for another new account.  
        private void btnAddAnotherAccount_Click(object sender, EventArgs e)  
        {  
            this.ClearForm();  
        }  
  
        //NC-28 Clear values from controls.  
        private void ClearForm()  
        {  
            txtCustomerName.Clear();  
            txtCustomerID.Clear();  
            dtpOrderDate.Value = DateTime.Now;  
            numOrderAmount.Value = 0;  
            this.parsedCustomerID = 0;  
        }  
  
        //NC-29 Close the form.  
        private void btnAddFinish_Click(object sender, EventArgs e)  
        {  
            this.Close();  
        }  
  
    }  
}  
  
```  
  
```vb  
Imports System  
Imports System.Collections.Generic  
Imports System.ComponentModel  
Imports System.Data  
Imports System.Drawing  
Imports System.Linq  
Imports System.Text  
Imports System.Threading.Tasks  
Imports System.Windows.Forms  
' NC-1 More namespaces.  
Imports System.Data.SqlClient  
Imports System.Configuration  
  
Namespace SimpleDataApp  
    Partial Public Class NewCustomer  
        Inherits Form  
  
        ' NC-2 Storage for IDENTITY values returned from database.  
        Private parsedCustomerID As Integer  
        Private orderID As Integer  
  
        ' NC-3 Specify a connection string.  
        Private connstr As String = SimpleDataApp.Utility.GetConnectionString()  
  
        Public Sub New()  
            InitializeComponent()  
        End Sub  
  
        ' NC-4 Create account.  
        Private Sub btnCreateAccount_Click() Handles btnCreateAccount.Click  
  
            ' NC-5 Set up and run stored procedure only if Customer Name is present.  
            If isCustomerName() Then  
  
                ' NC-6 Create the connection.  
                Dim conn As New SqlConnection(connstr)  
  
                ' NC-7 Create a SqlCommand, and identify it as a stored procedure.  
                Dim cmdNewCustomer As New SqlCommand("Sales.uspNewCustomer", conn)  
                cmdNewCustomer.CommandType = CommandType.StoredProcedure  
  
                ' NC-8 Add input parameter from the stored procedure and specify what to use as its value.  
                cmdNewCustomer.Parameters.Add(New SqlParameter("@CustomerName", SqlDbType.NVarChar, 40))  
                cmdNewCustomer.Parameters("@CustomerName").Value = txtCustomerName.Text  
  
                ' NC-9 Add output parameter.  
                cmdNewCustomer.Parameters.Add(New SqlParameter("@CustomerID", SqlDbType.Int))  
                cmdNewCustomer.Parameters("@CustomerID").Direction = ParameterDirection.Output  
  
                ' NC-10 try-catch-finally  
                Try  
                    ' NC-11 Open the connection.  
                    conn.Open()  
  
                    ' NC-12 Run the stored procedure.  
                    cmdNewCustomer.ExecuteNonQuery()  
  
                    ' NC-13 Customer ID is an IDENTITY value from the database.   
                    Me.parsedCustomerID = CInt(cmdNewCustomer.Parameters("@CustomerID").Value)  
                    Me.txtCustomerID.Text = Convert.ToString(parsedCustomerID)  
  
                Catch  
                    ' NC-14 A simple catch.  
                    MessageBox.Show("Customer ID was not returned. Account could not be created.")  
                Finally  
                    ' NC-15 Close the connection.  
                    conn.Close()  
                End Try  
            End If  
        End Sub  
  
        ' NC-16 Verify that Customer Name is present.  
        Private Function isCustomerName() As Boolean  
            If txtCustomerName.Text = "" Then  
                MessageBox.Show("Please enter a name.")  
                Return False  
            Else  
                Return True  
            End If  
        End Function  
  
        ' NC-17 Place order.  
        Private Sub btnPlaceOrder_Click() Handles btnPlaceOrder.Click  
  
            ' NC-18 Set up and run stored procedure only if necessary input is present.  
            If isPlaceOrderReady() Then  
  
                ' Create the connection.  
                Dim conn As New SqlConnection(connstr)  
  
                ' NC-19 Create SqlCommand and identify it as a stored procedure.  
                Dim cmdNewOrder As New SqlCommand("Sales.uspPlaceNewOrder", conn)  
                cmdNewOrder.CommandType = CommandType.StoredProcedure  
  
                ' NC-20 @CustomerID, which was an output parameter from uspNewCustomer.  
                cmdNewOrder.Parameters.Add(New SqlParameter("@CustomerID", SqlDbType.Int))  
                cmdNewOrder.Parameters("@CustomerID").Value = Me.parsedCustomerID  
  
                ' NC-21 @OrderDate.  
                cmdNewOrder.Parameters.Add(New SqlParameter("@OrderDate", SqlDbType.DateTime, 8))  
                cmdNewOrder.Parameters("@OrderDate").Value = dtpOrderDate.Value  
  
                ' NC-22 @Amount.  
                cmdNewOrder.Parameters.Add(New SqlParameter("@Amount", SqlDbType.Int))  
                cmdNewOrder.Parameters("@Amount").Value = numOrderAmount.Value  
  
                ' NC-23 @Status. For a new order, the status is always O (open).  
                cmdNewOrder.Parameters.Add(New SqlParameter("@Status", SqlDbType.[Char], 1))  
                cmdNewOrder.Parameters("@Status").Value = "O"  
  
                ' NC-24 Add return value for stored procedure, which is orderID.  
                cmdNewOrder.Parameters.Add(New SqlParameter("@RC", SqlDbType.Int))  
                cmdNewOrder.Parameters("@RC").Direction = ParameterDirection.ReturnValue  
  
                ' try-catch-finally  
                Try  
                    ' Open connection.  
                    conn.Open()  
  
                    ' Run the stored procedure.  
                    cmdNewOrder.ExecuteNonQuery()  
  
                    ' NC-25 Display the order number.  
                    Me.orderID = CInt(cmdNewOrder.Parameters("@RC").Value)  
                    MessageBox.Show("Order number " & (Me.orderID).ToString & " has been submitted.")  
  
                Catch  
                    ' A simple catch.  
                    MessageBox.Show("Order could  not be placed.")  
  
                Finally  
                    ' Close connection.  
                    conn.Close()  
                End Try  
            End If  
        End Sub  
  
        ' NC-26 Verify that order data is ready.  
        Private Function isPlaceOrderReady() As Boolean  
  
            ' Verify that CustomerID is present.  
            If txtCustomerID.Text = "" Then  
                MessageBox.Show("Please create customer account before placing order.")  
                Return False  
  
                ' Verify that Amount isn't 0.   
            ElseIf (numOrderAmount.Value < 1) Then  
  
                MessageBox.Show("Please specify an order amount.")  
                Return False  
            Else  
                ' Order can be submitted.  
                Return True  
            End If  
        End Function  
  
        ' NC-27 Reset the form for another new account.  
        Private Sub btnAddAnotherAccount_Click() Handles btnAddAnotherAccount.Click  
            Me.ClearForm()  
        End Sub  
  
        ' NC-28 Clear values from controls.  
        Private Sub ClearForm()  
            txtCustomerName.Clear()  
            txtCustomerID.Clear()  
            dtpOrderDate.Value = DateTime.Now  
            numOrderAmount.Value = 0  
            Me.parsedCustomerID = 0  
        End Sub  
  
        ' NC-29 Close the form.  
        Private Sub btnAddFinish_Click() Handles btnAddFinish.Click  
            Me.Close()  
        End Sub  
  
    End Class  
End Namespace  
```  
  
|コメント|説明|  
|-------------|-----------------|  
|NC-1|追加`System.Data.SqlClient`と`System.Configuration`名前空間の一覧にします。|  
|NC-2|後で使用する `parsedCustomerID` および `orderID` の変数を宣言します。|  
|NC-3|アプリケーション構成ファイルから接続文字列を取得するための `GetConnectionString` のメソッドを呼び出し、`connstr` 文字列変数を格納します。|  
|NC-4|`btnCreateAccount` ボタンのクリック イベント ハンドラーのコードを追加します。|  
|NC-5|`isCustomerName` が顧客名の存在する場合にのみ実行されるように、クリック イベント コードの `uspNewCustomer` への呼び出しをラップします。|  
|NC-6|`SqlConnection` オブジェクト (`conn`) を作成し、`connstr` 接続文字列に渡します。|  
|NC-7|`SqlCommand` オブジェクト `cmdNewCustomer` を作成します。<br /><br /> -指定`Sales.uspNewCustomer`としてストアド プロシージャを実行します。<br />-を使用して、`CommandType`コマンドがストアド プロシージャであることを指定するプロパティ。|  
|NC-8|ストアド プロシージャからの `@CustomerName` 入力パラメーターを追加します。<br /><br /> パラメーターを追加、`Parameters`コレクション。<br />-を使用して、 `SqlDbType` nvarchar (40) として、パラメーターの型を指定する列挙体。<br />-指定`txtCustomerName.Text`ソースとして。|  
|NC-9|ストアド プロシージャからの出力パラメーターを追加します。<br /><br /> パラメーターを追加、`Parameters`コレクション。<br />-使用`ParameterDirection.Output`を出力としてパラメーターを識別します。|  
|NC-10|接続を開き、ストアド プロシージャを実行、例外を処理し、接続を閉じます Try – Catch – Finally ブロックを追加します。|  
|NC-11|NC-6 で作成した接続 (`conn`) を開きます。|  
|NC-12|使用して、`ExecuteNonQuery`メソッド`cmdNewCustomer`を実行する、`Sales.uspNewCustomer`ストアド プロシージャ。 これは、ストアド プロシージャを実行する`INSERT`ステートメントでは、クエリではありません。|  
|NC-13|データベースから IDENTITY 値として `@CustomerID` の値が戻されます。 これは、整数、ために表示されることで文字列に変換する必要があります、**顧客 ID**テキスト ボックス。<br /><br /> -宣言して`parsedCustomerID`nc-2 でします。<br />-格納、`@CustomerID`値`parsedCustomerID`後で使用します。<br />-返される顧客 ID を文字列に変換し、それに挿入`txtCustomerID.Text`します。|  
|NC-14|このサンプルでは、単純な (実稼働品質のない) の catch 句を追加します。|  
|NC-15|使用の終了後必ず接続を閉じ、接続プールに解放できるようします。 参照してください[SQL Server の接続プール (ADO.NET)](http://msdn.microsoft.com/library/8xx3tyca\(l=en-us,v=VS.110\).aspx)します。|  
|NC-16|顧客名が存在することを確認するメソッドを定義します。<br /><br /> -テキスト ボックスが空の場合、メッセージが表示され、返す`false`名前がアカウントを作成するために必要なためです。<br />-テキスト ボックスが空でない場合は、返す`true`します。|  
|NC-17|`btnPlaceOrder` ボタンのクリック イベント ハンドラーのコードを追加します。|  
|NC-18|必要な入力が存在しない場合に `isPlaceOrderReady` を実行しないように、`btnPlaceOrder_Click` イベント コードの `uspPlaceNewOrder` への呼び出しをラップします。|  
|NC-19 から NC-25|これらのセクションのコードは、`btnCreateAccount_Click` イベント ハンドラーに追加したコードと類似しています。<br /><br /> -NC-19。 `SqlCommand` オブジェクトの `cmdNewOrder` を作成し、ストアド プロシージャとして `Sales.uspPlaceOrder` を指定します。<br />NC-20 から nc-23 は、ストアド プロシージャの入力パラメーターです。<br />-NC-24 です。 `@RC` はデータベースから生成された注文 ID の戻り値を含みます。 このパラメーターの方向は `ReturnValue` として指定されます。<br />-NC-25 です。 Order ID (注文 ID) の値を NC-2 で宣言した `orderID` 変数に格納し、メッセージ ボックスに値を表示します。|  
|NC-26|Customer ID (顧客 ID) が存在すること、および `numOrderAmount` で Amount (数量) が指定されていることを確認するメソッドを定義します。|  
|NC-27|`ClearForm` イベント ハンドラーの `btnAddAnotherAccount` メソッドを呼び出します。|  
|NC-28|別の顧客を追加するために、フォームから値をクリアする `ClearForm` メソッドを作成します。|  
|NC29|NewCustomer フォームを閉じて、Navigation フォームにフォーカスを戻します。|  
  
### <a name="fillorcancel-form"></a>FillOrCancel フォーム  
 FillorCancel フォームは、注文 ID を入力します を選択すると、注文を返すクエリを実行、 **Find Order**ボタンをクリックします。 戻された行は読み取り専用なデータ グリッドに表示されます。 注文をキャンセル (X) をマークするには、選択した場合、 **Cancel Order**ボタンをクリック、としてマークできます順序満たした (F) を選択した場合、 **Fill Order**ボタンをクリックします。 選択した場合、 **Find Order**更新された行の表示を再度クリックします。  
  
#### <a name="create-event-handlers"></a>イベント ハンドラーを作成する  
 フォームのボタン 4 つに空のクリック イベント ハンドラーを作成します。  
  
#### <a name="create-code-for-fillorcancel"></a>FillOrCancel のコードを作成する  
 FillOrCancel フォームに次のコードを追加します。 番号付きコメントおよびコードに続くテーブルを使用して、コード ブロックをステップ実行します。  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.ComponentModel;  
using System.Data;  
using System.Drawing;  
using System.Linq;  
using System.Text;  
using System.Threading.Tasks;  
using System.Windows.Forms;  
//FC-1 More namespaces.  
using System.Text.RegularExpressions;  
using System.Data.SqlClient;  
using System.Configuration;  
  
namespace SimpleDataApp  
{  
    public partial class FillOrCancel : Form  
    {  
        //FC-2 Storage for OrderID.  
        private int parsedOrderID;  
  
        //FC-3 Specify a connection string.  
        string connstr = SimpleDataApp.Utility.GetConnectionString();  
  
        public FillOrCancel()  
        {  
            InitializeComponent();  
        }  
  
        //FC-4 Find an order.  
        private void btnFindByOrderID_Click(object sender, EventArgs e)  
        {  
            //FC-5 Prepare the connection and the command.  
            if (isOrderID())  
            {  
                //Create the connection.  
                SqlConnection conn = new SqlConnection(connstr);  
  
                //Define a query string that has a parameter for orderID.  
                string sql = "select * from Sales.Orders where orderID = @orderID";  
  
                //Create a SqlCommand object.  
                SqlCommand cmdOrderID = new SqlCommand(sql, conn);  
  
                //Define the @orderID parameter and its value.  
                cmdOrderID.Parameters.Add(new SqlParameter("@orderID", SqlDbType.Int));  
                cmdOrderID.Parameters["@orderID"].Value = parsedOrderID;  
  
                //try-catch-finally  
                try  
                {  
                    //FC-6 Run the command and display the results.  
                    //Open the connection.  
                    conn.Open();  
  
                    //Run the command by using SqlDataReader.  
                    SqlDataReader rdr = cmdOrderID.ExecuteReader();  
  
                    //Create a data table to hold the retrieved data.  
                    DataTable dataTable = new DataTable();  
  
                    //Load the data from SqlDataReader into the data table.  
                    dataTable.Load(rdr);  
  
                    //Display the data from the data table in the data grid view.  
                    this.dgvCustomerOrders.DataSource = dataTable;  
  
                    //Close the SqlDataReader.  
                    rdr.Close();  
                }  
                catch  
                {  
                    //A simple catch.  
                    MessageBox.Show("The requested order could not be loaded into the form.");  
                }  
                finally  
                {  
                    //Close the connection.  
                    conn.Close();  
                }  
            }  
        }  
  
        //FC-7 Cancel an order.  
        private void btnCancelOrder_Click(object sender, EventArgs e)  
        {  
            //Set up and run stored procedure only if OrderID is ready.  
            if (isOrderID())  
            {  
                //Create the connection.  
                SqlConnection conn = new SqlConnection(connstr);  
  
                // Create command and identify it as a stored procedure.  
                SqlCommand cmdCancelOrder = new SqlCommand("Sales.uspCancelOrder", conn);  
                cmdCancelOrder.CommandType = CommandType.StoredProcedure;  
  
                cmdCancelOrder.Parameters.Add(new SqlParameter("@orderID", SqlDbType.Int));  
                cmdCancelOrder.Parameters["@orderID"].Value = parsedOrderID;  
  
                // try-catch-finally  
                try  
                {  
                    // Open the connection.  
                    conn.Open();  
  
                    // Run the cmdCancelOrder command.  
                    cmdCancelOrder.ExecuteNonQuery();  
                }  
                // A simple catch.  
                catch  
                {  
                    MessageBox.Show("The cancel operation was not completed.");  
                }  
                finally  
                {  
                    //Close connection.  
                    conn.Close();  
                }  
            }  
        }  
  
        //FC-8 Fill an order.  
        private void btnFillOrder_Click(object sender, EventArgs e)  
        {  
            //Set up and run stored procedure only if OrderID is ready.  
            if (isOrderID())  
            {  
                //Create the connection.  
                SqlConnection conn = new SqlConnection(connstr);  
  
                //Create command and identify it as a stored procedure.  
                SqlCommand cmdFillOrder = new SqlCommand("Sales.uspFillOrder", conn);  
                cmdFillOrder.CommandType = CommandType.StoredProcedure;  
  
                // Add input parameter from the stored procedure.  
                cmdFillOrder.Parameters.Add(new SqlParameter("@orderID", SqlDbType.Int));  
                cmdFillOrder.Parameters["@orderID"].Value = parsedOrderID;  
  
                //Add the second input parameter.  
                cmdFillOrder.Parameters.Add(new SqlParameter("@FilledDate", SqlDbType.DateTime, 8));  
                cmdFillOrder.Parameters["@FilledDate"].Value = dtpFillDate.Value;  
  
                //try-catch-finally  
                try  
                {  
                    //Open the connection.  
                    conn.Open();  
  
                    //Run the cmdFillOrder command.  
                    cmdFillOrder.ExecuteNonQuery();  
                }  
                catch  
                {  
                    //A simple catch.  
                    MessageBox.Show("The fill operation was not completed.");  
                }  
                finally  
                {  
                    //Close the connection.  
                    conn.Close();  
                }  
            }  
        }  
  
        //FC-9 Verify that OrderID is ready.  
        private bool isOrderID()  
        {  
  
            //Check for input in the Order ID text box.  
            if (txtOrderID.Text == "")  
            {  
                MessageBox.Show("Please specify the Order ID.");  
                return false;  
            }  
  
            // Check for characters other than integers.  
            else if (Regex.IsMatch(txtOrderID.Text, @"^\D*$"))  
            {  
               //Show message and clear input.  
                MessageBox.Show("Please specify integers only.");  
                txtOrderID.Clear();  
                return false;  
            }  
            else  
            {  
                //Convert the text in the text box to an integer to send to the database.  
                parsedOrderID = Int32.Parse(txtOrderID.Text);  
                return true;  
            }  
        }  
  
        //Close the form.  
        private void btnFinishUpdates_Click(object sender, EventArgs e)  
        {  
            this.Close();  
        }  
    }  
}  
```  
  
```vb  
Imports System  
Imports System.Collections.Generic  
Imports System.ComponentModel  
Imports System.Data  
Imports System.Drawing  
Imports System.Linq  
Imports System.Text  
Imports System.Threading.Tasks  
Imports System.Windows.Forms  
' FC-1 More namespaces.  
Imports System.Text.RegularExpressions  
Imports System.Data.SqlClient  
Imports System.Configuration  
  
Namespace SimpleDataApp  
    Partial Public Class FillOrCancel  
        Inherits Form  
        ' FC-2 Storage for OrderID.  
        Private parsedOrderID As Integer  
  
        ' FC-3 Specify a connection string.  
        Private connstr As String = SimpleDataApp.Utility.GetConnectionString()  
  
        Public Sub New()  
            InitializeComponent()  
        End Sub  
  
        ' FC-4 Find an order.  
        Private Sub btnFindByOrderID_Click() Handles btnFindByOrderID.Click  
  
            ' FC-5 Prepare the connection and the command.  
  
            If isOrderID() Then  
                ' Create the connection.  
                Dim conn As New SqlConnection(connstr)  
  
                ' Define the query string that has a parameter for orderID.  
                Dim sql As String = "select * from Sales.Orders where orderID = @orderID"  
  
                ' Create a SqlCommand object.  
                Dim cmdOrderID As New SqlCommand(sql, conn)  
  
                ' Define the @orderID parameter and its value.  
                cmdOrderID.Parameters.Add(New SqlParameter("@orderID", SqlDbType.Int))  
                cmdOrderID.Parameters("@orderID").Value = parsedOrderID  
  
                ' try-catch-finally  
                Try  
                    ' FC-6 Run the command and display the results.  
                    ' Open connection.  
                    conn.Open()  
  
                    ' Run the command by using SqlDataReader.  
                    Dim rdr As SqlDataReader = cmdOrderID.ExecuteReader()  
  
                    ' Create a data table to hold the retrieved data.  
                    Dim dataTable As New DataTable()  
  
                    ' Load the data from SqlDataReader into the data table.  
                    dataTable.Load(rdr)  
  
                    ' Display the data from the data table in the data grid view.  
                    Me.dgvCustomerOrders.DataSource = dataTable  
  
                    ' Close the SqlDataReader.  
                    rdr.Close()  
                Catch  
                    ' A simple catch.  
                    MessageBox.Show("The requested order could not be loaded into the form.")  
                Finally  
                    ' Close the connection.  
                    conn.Close()  
                End Try  
            End If  
        End Sub  
  
        ' FC-7 Cancel an order.  
        Private Sub btnCancelOrder_Click() Handles btnCancelOrder.Click  
  
            ' Set up and run stored procedure only if OrderID is ready.  
            If isOrderID() Then  
  
                ' Create the connection.  
                Dim conn As New SqlConnection(connstr)  
  
                ' Create the command and identify it as a stored procedure.  
                Dim cmdCancelOrder As New SqlCommand("Sales.uspCancelOrder", conn)  
                cmdCancelOrder.CommandType = CommandType.StoredProcedure  
  
                ' Add input parameter from the stored procedure.  
                cmdCancelOrder.Parameters.Add(New SqlParameter("@orderID", SqlDbType.Int))  
                cmdCancelOrder.Parameters("@orderID").Value = parsedOrderID  
  
                ' try-catch-finally  
                Try  
                    ' Open the connection.  
                    conn.Open()  
  
                    ' Run the cmdCancelOrder command.  
                    cmdCancelOrder.ExecuteNonQuery()  
                Catch  
                    ' A simple catch.  
                    MessageBox.Show("The cancel operation was not completed.")  
                Finally  
                    ' Close connection.  
                    conn.Close()  
                End Try  
            End If  
        End Sub  
  
        ' FC-8 Fill an order.  
        Private Sub btnFillOrder_Click() Handles btnFillOrder.Click  
  
            ' Set up and run stored procedure only if OrderID is ready.  
            If isOrderID() Then  
  
                ' Create the connection.  
                Dim conn As New SqlConnection(connstr)  
  
                ' Create command and identify it as a stored procedure.  
                Dim cmdFillOrder As New SqlCommand("Sales.uspFillOrder", conn)  
                cmdFillOrder.CommandType = CommandType.StoredProcedure  
  
                ' Add input parameter from the stored procedure.  
                cmdFillOrder.Parameters.Add(New SqlParameter("@orderID", SqlDbType.Int))  
                cmdFillOrder.Parameters("@orderID").Value = parsedOrderID  
  
                ' Add second input parameter.  
                cmdFillOrder.Parameters.Add(New SqlParameter("@FilledDate", SqlDbType.DateTime, 8))  
                cmdFillOrder.Parameters("@FilledDate").Value = dtpFillDate.Value  
  
                ' try-catch-finally  
                Try  
                    ' Open the connection.  
                    conn.Open()  
  
                    ' Run the cmdFillOrder command.   
                    cmdFillOrder.ExecuteNonQuery()  
                Catch  
                    ' A simple catch.  
                    MessageBox.Show("The fill operation was not completed.")  
                Finally  
                    ' Close the connection.  
                    conn.Close()  
                End Try  
            End If  
        End Sub  
  
        ' FC-9 Verify that OrderID is ready.  
        Private Function isOrderID() As Boolean  
  
            ' Check for input in the Order ID text box.  
            If txtOrderID.Text = "" Then  
                MessageBox.Show("Please specify the Order ID.")  
                Return False  
  
                ' Check for characters other than integers.  
            ElseIf Regex.IsMatch(txtOrderID.Text, "^\D*$") Then  
  
                ' Show message and clear input.  
                MessageBox.Show("Please specify integers only.")  
                txtOrderID.Clear()  
                Return False  
  
            Else  
                ' Convert the text in the text box to an integer to send to the database.  
                parsedOrderID = Int32.Parse(txtOrderID.Text)  
                Return True  
  
            End If  
        End Function  
  
        ' Close the form.  
        Private Sub btnFinishUpdates_Click() Handles btnFinishUpdates.Click  
            Me.Close()  
        End Sub  
    End Class  
End Namespace  
```  
  
|コメント|説明|  
|-------------|-----------------|  
|FC-1|追加`System.Data.SqlClient`、 `System.Configuration`、および`System.Text.RegularExpressions`名前空間の一覧にします。|  
|FC-2|変数 `parsedOrderID` を宣言します。|  
|FC-3|アプリケーション構成ファイルから接続文字列を取得するための `GetConnectionString` のメソッドを呼び出し、`connstr` 文字列変数を格納します。|  
|FC-4|`btnFindOrderByID` のクリック イベント ハンドラーのコードを追加します。|  
|FC-5|これらのタスクは SQL ステートメントまたはストアド プロシージャを実行する前に必要です。<br /><br /> -作成、`SqlConnection`オブジェクト。<br />SQL ステートメントを定義またはストアド プロシージャの名前を指定します。 (ここでは、`SELECT` ステートメントを実行します。)<br />-作成、`SqlCommand`オブジェクト。<br />-SQL ステートメントまたはストアド プロシージャのパラメーターを定義します。|  
|FC-6|このコードは、クエリの結果を取得して表示するために `SqlDataReader` および `DataTable` を使用します。<br /><br /> -接続を開きます。<br />-作成、`SqlDataReader`オブジェクト、`rdr`を実行して、`ExecuteReader`メソッド`cmdOrderID`します。<br />-作成、`DataTable`取得したデータを保持するオブジェクト。<br />-からデータを読み込み、`SqlDataReader`オブジェクトを`DataTable`オブジェクト。<br />-データを表示、データ グリッド ビューで指定することによって`DataTable`として`DataSource`データ グリッド ビューの。<br />-閉じる`SqlDataReader`します。|  
|FC-7|`btnCancelOrder` のクリック イベント ハンドラーのコードを追加します。 このコードは `Sales.uspCancelOrder` ストアド プロシージャを実行します。|  
|FC-8|`btnFillOrder` のクリック イベント ハンドラーのコードを追加します。 このコードは `Sales.uspFillOrder` ストアド プロシージャを実行します。|  
|FC-9|いることを確認するメソッドを作成`OrderID`へのパラメーターとして送信する準備ができて、`SqlCommand`オブジェクト。<br /><br /> -で、ID が入力されていることを確認して`txtOrderID`します。<br />-使用`Regex.IsMatch`整数以外の文字の簡単なチェックを定義します。<br />-宣言して、 `parsedOrderID` fc-2 で変数。<br />-入力が有効な場合、テキストを整数に変換しに値を格納、`parsedOrderID`変数。<br />-ラップ、`isOrderID`に関するメソッド、 `btnFindByOrderID`、 `btnCancelOrder`、および`btnFillOrder`クリックしてイベント ハンドラー。|  
  
##  <a name="BKMK_testyourapplication"></a> アプリケーションをテストします。  
 ビルドし、各クリック イベント ハンドラーのコードを記述した後、アプリケーションをテストするには、F5 キーを選択し、コーディングを完了した後、します。

