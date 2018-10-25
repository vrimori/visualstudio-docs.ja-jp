---
title: Visual Studio での診断データ アダプター作成用のサンプル プロジェクト
ms.date: 10/19/2016
ms.topic: sample
helpviewer_keywords:
- Diagnostic Data Adapter [Visual Studio ALM]
- samples. Diagnostic Data Adapter [Visual Studio ALM]
- Diagnostic Data Adapter, sample
ms.assetid: 548bdc5e-338f-4be7-a555-e6a2efb1df6b
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 421f49ec9cfca99a62b80ddf71073a481b3a0c7e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49878207"
---
# <a name="sample-project-for-creating-a-diagnostic-data-adapter"></a>診断データ アダプター作成用のサンプル プロジェクト

"MyDiagnosticDataAdapter" は、テストを実行したときに、テスト結果にログ ファイルを添付できる簡単な診断データ アダプターです。

 診断データ コレクターまたは構成エディターがインストールされているコンピューターの管理アクセス許可が必要です。

## <a name="example-data-adapter"></a>データ アダプターの例

このサンプルは、次のタスクを実行する方法を示します。

-   属性を適用し、Microsoft Test Manager がクラスを診断データ アダプターとして検出できるようにする。

-   属性を適用し、Microsoft Test Manager がユーザー コントロール クラスをエディターとして検出し、診断データ アダプター用の構成を変更して使用できるようにする。

-   既定の構成データにアクセスする。

-   特定の診断データ収集イベントに登録する。

-   ログ ファイルを <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionSink> に送信して添付する。

```csharp
// My Data Collector Class
using Microsoft.VisualStudio.TestTools.Common;
using Microsoft.VisualStudio.TestTools.Execution;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Xml;
using System;

namespace MyCompany.MyDiagnosticDataAdapters
{
    // Provide a URI and friendly name for your diagnostic data adapter
    [DataCollectorTypeUri("datacollector://MyCompany/MyDataCollector/1.0")]
    [DataCollectorFriendlyName("Collect Log Files sample", false)]
    // Designate your chosen configuration editor
    [DataCollectorConfigurationEditor(
        "configurationeditor://MyCompany/MyDataConfigEditor/1.0")]
    public class MyDataCollector : DataCollector
    {
        private DataCollectionEvents dataEvents;
        private DataCollectionLogger dataLogger;
        private DataCollectionSink dataSink;
        private XmlElement configurationSettings;

        // Required method called by the testing framework
        public override void Initialize(
            XmlElement configurationElement,
            DataCollectionEvents events,
            DataCollectionSink sink,
            DataCollectionLogger logger,
            DataCollectionEnvironmentContext environmentContext)
        {
            dataEvents = events; // The test events
            dataLogger = logger; // The error and warning log
            dataSink = sink;     // Saves collected data
            // Configuration from the test settings
            configurationSettings = configurationElement;

            // Register common events for the data collector
            // Not all of the events are used in this class
            dataEvents.SessionStart +=
                new EventHandler<SessionStartEventArgs>(OnSessionStart);
            dataEvents.SessionEnd +=
                new EventHandler<SessionEndEventArgs>(OnSessionEnd);
            dataEvents.TestCaseStart +=
                new EventHandler<TestCaseStartEventArgs>(OnTestCaseStart);
            dataEvents.TestCaseEnd +=
                new EventHandler<TestCaseEndEventArgs>(OnTestCaseEnd);
            dataEvents.DataRequest +=
                new EventHandler<DataRequestEventArgs>(OnDataRequest);
        }

        protected override void Dispose(bool disposing)
        {
            if (disposing)
            {
                dataEvents.SessionStart -=
                    new EventHandler<SessionStartEventArgs>(OnSessionStart);
                dataEvents.SessionEnd -=
                    new EventHandler<SessionEndEventArgs>(OnSessionEnd);
                dataEvents.TestCaseStart -=
                    new EventHandler<TestCaseStartEventArgs>(OnTestCaseStart);
                dataEvents.TestCaseEnd -=
                    new EventHandler<TestCaseEndEventArgs>(OnTestCaseEnd);
                dataEvents.DataRequest -=
                    new EventHandler<DataRequestEventArgs>(OnDataRequest);
            }
        }

        #region Event Handlers
        public void OnSessionStart(object sender, SessionStartEventArgs e)
        {
            // TODO: Provide implementation
        }

        public void OnSessionEnd(object sender, SessionEndEventArgs e)
        {
            // TODO: Provide implementation
        }

        public void OnTestCaseStart(object sender, TestCaseEventArgs e)
        {
            // TODO: Provide implementation
        }

        public void OnTestCaseEnd(object sender, TestCaseEndEventArgs e)
        {
            // Get any files to be collected that are
            // configured in your test settings
            List<string> files = getFilesToCollect();

            // For each of the files, send the file to the data sink
            // which will attach it to the test results or to a bug
            foreach (string file in files)
            {
                dataSink.SendFileAsync(e.Context, file, false);
            }
        }

        public void OnDataRequest(object sender, DataRequestEventArgs e)
        {
            // TODO: Provide implementation
            // Most likely this occurs because a bug is being filed
        }
        #endregion

        // A private method to collect the configured file names
        private List<string> getFilesToCollect()
        {
            // Seetup namespace manager with our namespace
            XmlNamespaceManager nsmgr =
                new XmlNamespaceManager(
                    configurationSettings.OwnerDocument.NameTable);
            nsmgr.AddNamespace("ns",
                "http://MyCompany/schemas/MyDataCollector/1.0");

            // Find all of the "File" elements under our configuration
            XmlNodeList files =
                configurationSettings.SelectNodes(
                    "//ns:MyDataCollector/ns:File");

            // Build the list of files to collect from the
            // "FullPath" attributes of the "File" nodes.
            List<string> result = new List<string>();
            foreach (XmlNode fileNode in files)
            {
                XmlAttribute pathAttribute =
                    fileNode.Attributes["FullPath"];
                if (pathAttribute != null &&
                    !String.IsNullOrEmpty(pathAttribute.Value))
                {
                    result.Add(pathAttribute.Value);
                }
            }

            return result;
        }
    }
}
```

## <a name="example-configuration-editor"></a>構成エディターの例

これは、診断データ アダプター用のサンプルの構成エディターです。 ユーザー コントロールをプロジェクトに追加し、"ログ ファイル名:" というラベルと "FileTextBox" という名前のテキスト ボックスを持つ非常にシンプルなフォームを作成します。

```csharp
using Microsoft.VisualStudio.TestTools.Common;
using Microsoft.VisualStudio.TestTools.Execution;
using System.Collections.Generic;
using System.ComponentModel;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Windows.Forms;
using System.Xml;
using System;

namespace MyCompany.DiagnosticDataAdapters.ConfigurationEditors
{
    [DataCollectorConfigurationEditorTypeUri(
        "configurationeditor://MyCompany/MyConfigEditor/1.0")]
    public partial class MyDataConfigEditor :
        UserControl, IDataCollectorConfigurationEditor
    {
        private DataCollectorSettings collectorSettings;

        // Create a private property for the service provider
        private IServiceProvider ServiceProvider { get; set; }

        // Constructor
        public MyConfigurationEditor()
        {
            InitializeComponent();
        }

        // Required method called by the testing framework
        public void Initialize(
            IServiceProvider svcProvider,
            DataCollectorSettings settings)
        {
            ServiceProvider = svcProvider;
            collectorSettings = settings;

            // Display the file name as listed in the settings file.
            // If the configuration has not been updated before, this
            // data will be provided by the default configuration
            // section from <nameofcollector>.dll.config:
            // <DefaultConfiguration>
            //   <MyCollectorName
            //       xmlns="http://MyCompany/schemas/ProductName/Version");
            //     <File FullPath="C:\temp\logfile1.txt" />
            //   </MyCollectorName>
            // </DefaultConfiguration>
            this.SuspendLayout();
            this.FileTextBox.Text = GetText(collectorSettings.Configuration);
            this.ResumeLayout();
        }

        // Can be used to verify data before saving it
        public bool VerifyData()
        {
            // Not currently verifying data
            return true;
        }

        // Reset to default value from XML configuration
        // using a custom method
        public void ResetToAgentDefaults()
        {
            this.FileTextBox.Text =
                getText(collectorSettings.DefaultConfiguration);
        }

        // Saves data changed in the editor to the test configuration
        // settings. Does not change the default value.
        public DataCollectorSettings SaveData()
        {
            collectorSettings.Configuration.InnerXml =
                String.Format(
                    @"<MyCollectorName
      xmlns=""http://MyCompany/schemas/MyDataCollector/1.0"">
  <File FullPath=""{0}"" />
</MyCollectorName>",
                    FileTextBox.Text);
            return collectorSettings;
        }

        // Reads the configuration settings
        private string getText(XmlElement element)
        {
            // Setup namespace manager with our namespace
            XmlNamespaceManager nsmgr =
                new XmlNamespaceManager(
                    element.OwnerDocument.NameTable);

            // Find all the "File" elements under our configuration
            XmlNodeList files = element.SelectNodes("//ns:MyDataCollector/ns:File", nsmgr);

            string result = String.Empty;
            if (files.Count > 0)
            {
                XmlAttribute pathAttribute = files[0].Attributes["FullPath"];
                if (pathAttribute != null &&
                    !String.IsNullOrEmpty(pathAttribute.Value))
                {
                    result = pathAttribute.Value;
                }
            }

            return result;
        }
    }
}
```

## <a name="example-configuration-file"></a>構成ファイルの例

次に、診断データ コレクターの構成エディター用のサンプル構成ファイルを示します。

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <configSections>
    <section
      name="DataCollectorConfiguration"
      type="Microsoft.VisualStudio.QualityTools.Execution.DataCollectorConfigurationSection,
        Microsoft.visualStudio.QualityTools.ExecutionCommon,
        Version=4.0.0.0, Culture=neutral,
        PublicKeyToken=b03f5f7f11d50a3a" />
  </configSections>
  <DataCollectorConfiguration
      xmlns="http://microsoft.com/schemas/VisualStudio/TeamTest/11">
    <DataCollector
        typeUri="datacollector://MyCompany/MyDataCollector/1.0">
      <DefaultConfiguration>
        <!-- Your default config settings-->
        <File FullPath="c:\temp\logfile1.txt" />
      </DefaultConfiguration>
    </DataCollector>
  </DataCollectorConfiguration>
</configuration>
```

## <a name="compile-the-code"></a>コードのコンパイル

### <a name="to-create-the-code-project-for-this-diagnostic-adapter"></a>この診断アダプター用のコード プロジェクトを作成するには

1.  "MyDataCollector" という名前の新しいクラス ライブラリ プロジェクトを作成します。

2.  **ソリューション エクスプローラー**でプロジェクトを右クリックし、**[プロパティ]** をクリックします。 追加するフォルダーを選択するために、**[参照パス]** をクリックし、省略記号 (**…**) をクリックします。

     **[参照パスの選択]** ダイアログ ボックスが表示されます。

3.  インストール ディレクトリに基づき、パス *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\PrivateAssemblies* を選択します。 **[OK]** をクリックします。

4.  フォルダーを参照パスに追加するために、**[フォルダーの追加]** をクリックします。

     フォルダーが、参照パスの一覧に表示されます。

5.  **[すべてを保存]** アイコンをクリックして参照パスを保存します。

6.  アセンブリ **Microsoft.VisualStudio.QualityTools.ExecutionCommon** を追加します。

    1.  **ソリューション エクスプローラー**で、**[参照設定]** を右クリックし、**[参照の追加]** をクリックします。

    2.  **[参照]** を選択し、**Microsoft.VisualStudio.QualityTools.ExecutionCommon.dll** を探します。

         このアセンブリは *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\PrivateAssemblies* にあります。

    3.  **[OK]** をクリックします。

7.  アセンブリ **Microsoft.VisualStudio.QualityTools.Common** を追加します。

    1.  **ソリューション エクスプローラー**で、**[参照]** を右クリックし、**[参照の追加]** を選択します。

    2.  **[参照]** を選択し、**Microsoft.VisualStudio.QualityTools.Common.dll** を探します。

         このアセンブリは *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\PrivateAssemblies* にあります。

    3.  **[OK]** をクリックします。

8.  このドキュメントで既に示した診断データ アダプター クラスをクラス ライブラリのクラスにコピーします。 このクラスを保存します。

9. ユーザー コントロールをプロジェクトに追加するために、**ソリューション エクスプローラー**の **MyDataCollector** プロジェクトを右クリックし、**[追加]** をポイントします。次に、**[ユーザー コントロール]** を選択します。 **[追加]** をクリックします。

10. ツールボックスを使用して、ラベルをユーザー コントロールに追加し、Text プロパティを **ファイル名:** に変更します。

11. ツールボックスを使用して、テキスト ボックスをユーザー コントロールに追加し、名前を **textBoxFileName** に変更します。

12. **ソリューション エクスプローラー**でユーザー コントロールを右クリックし、**[コードの表示]** をクリックします。 このユーザー コントロール クラスを、このドキュメントで既に示したユーザー コントロール クラスに置き換えます。 このクラスを保存します。

    > [!NOTE]
    > 既定では、ユーザー コントロールに UserControl1 という名前が付けられます。 ユーザー コントロール クラスのコードでユーザー コントロールの名前が使用されていることを確認してください。

13. 構成ファイルを作成するために、**ソリューション エクスプローラー**でソリューションを右クリックし、**[追加]** をポイントします。次に、**[新しい項目]** をクリックします。 **[アプリケーション構成ファイル]** をクリックして選択し、**[追加]** をクリックします。 これにより、*App.config* という名前のファイルがソリューションに追加されます。

14. 前に提供されたサンプルから XML ファイルに XML をコピーします。 ファイルを保存します。

15. ソリューションをビルドし、ビルドしたアセンブリと *App.config* ファイルを *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\PrivateAssemblies\DataCollectors* ディレクトリにコピーします。

16. このカスタム診断データ アダプターを使用するテストの設定を作成します。 テストの設定を構成し、存在しているファイルを収集します。

     Microsoft Test Manager からテストを実行する場合は、テストを実行する前にこれらのテストの設定をテスト計画に割り当てるか、[オプションを指定して実行] コマンドを使用して、テストの設定の割り当ておよびオーバーライドを行います。 テスト設定の詳細については、「[テスト設定を使用して診断情報を収集する](../test/collect-diagnostic-information-using-test-settings.md)」を参照してください。

17. この診断データ アダプターを選択したテストの設定を使用して、テストを実行します。

     テストを実行したときに、指定したデータ ファイルがテスト結果に関連付けられます。

## <a name="see-also"></a>関連項目

- [方法: 診断データ アダプターを作成する](../test/how-to-create-a-diagnostic-data-adapter.md)
- [方法: 診断データ アダプター用のデータのカスタム エディターを作成する](../test/how-to-create-a-custom-editor-for-data-for-your-diagnostic-data-adapter.md)
- [方法: カスタム診断データ アダプターをインストールする](../test/how-to-install-a-custom-diagnostic-data-adapter.md)
- [診断データ アダプターを作成してカスタム データを収集する、またはテスト コンピューターに影響を与える](../test/create-a-diagnostic-data-adapter-to-collect-custom-data-or-affect-a-test-machine.md)