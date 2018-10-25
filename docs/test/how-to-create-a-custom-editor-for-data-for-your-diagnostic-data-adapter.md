---
title: Visual Studio で診断データ アダプター用のカスタム データ エディターを作成する
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Diagnostic Data Adapter, creating custom editor
ms.assetid: 24970227-d1ea-4f6d-9839-e911478848ba
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 41008d1c2808a5a6e6428670a3e7dbbf1041caee
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49819340"
---
# <a name="how-to-create-a-custom-editor-for-data-for-your-diagnostic-data-adapter"></a>方法: 診断データ アダプター用のデータのカスタム エディターを作成する

診断データ アダプターを作成する場合、テストの設定でそのカスタム診断データ アダプターが選択されているときにエンド ユーザーが特定のデータを構成できるようにすることができます。 たとえば、抽出するレジストリ キー、シミュレートするネットワーク負荷のレベル、または添付する一時ファイルや作業ファイルを検索するディレクトリを指定する構成データを選択できます。

診断データ アダプターの初期値を設定するには、構成ファイルを使用する必要があります。 ユーザーが構成データを変更するためのカスタム エディターを提供できます。

独自のエディターを作成するには、<xref:Microsoft.VisualStudio.TestTools.Execution.IDataCollectorConfigurationEditor> を実装するユーザー コントロールを作成します。

診断データ アダプターで <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorConfigurationEditorAttribute> を使用して、診断データの構成設定の編集に使用するエディター クラスを指定できます。

使用する既定の構成データも指定できます。  既定の構成のサンプルについては、「[診断データ アダプター作成用のサンプル プロジェクト](../test/sample-project-for-creating-a-diagnostic-data-adapter.md)」を参照してください。

カスタム データ診断アダプターを使用する際にテストの設定のデータを更新するためのカスタム エディターを作成するには、次の手順を実行します。

> [!NOTE]
> カスタム エディターを作成するには、まずクラスに <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorConfigurationEditorAttribute> が適用されている診断データ アダプターを作成する必要があります。 この属性でオプションの <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorConfigurationEditorAttribute.HelpUri*> プロパティを使用すると、エディターのヘルプ コンテンツ ソースを指定できます。 診断データ アダプターを作成する方法の詳細については、「[方法: カスタム診断データ アダプターを作成する](../test/how-to-create-a-diagnostic-data-adapter.md)」を参照してください。

カスタムの構成エディターを含む、診断データ アダプター プロジェクトのサンプル全体については、「[診断データ アダプター作成用のサンプル プロジェクト](../test/sample-project-for-creating-a-diagnostic-data-adapter.md)」を参照してください。

## <a name="to-create-a-custom-editor-for-your-diagnostic-data-adapter"></a>診断データ アダプター用のカスタム エディターを作成するには

1. プロジェクトにデータ診断アダプター用のユーザー コントロールを作成します。

   1.  診断データ アダプターのクラスを含むコード プロジェクトを右クリックし、**[追加]** をポイントし、**[ユーザー コントロール]** をポイントします。

   2.  この例では、"**Data File Name:**" というテキストが表示されたラベルおよび "**FileTextBox**" という名前のテキスト ボックスをフォームに追加して、ユーザーが必要なデータを入力できるようにします。

   > [!NOTE]
   > 現在、Windows フォームのユーザー コントロールだけがサポートされています。

2. 次の行を宣言セクションに追加します。

   ```csharp
   using System.Xml;
   using Microsoft.VisualStudio.TestTools.Common;
   using Microsoft.VisualStudio.TestTools.Execution;
   ```

3. このユーザー コントロールをカスタム エディターにします。

   1.  コード プロジェクト内でユーザー コントロールを右クリックし、**[コードの表示]** をポイントします。

   2.  次のようにして、エディターのインターフェイス <xref:Microsoft.VisualStudio.TestTools.Execution.IDataCollectorConfigurationEditor> を実装するようにクラスを設定します。

   ```csharp
   public partial class MyDataConfigEditor :
        UserControl, IDataCollectorConfigurationEditor
   ```

   1.  コードで <xref:Microsoft.VisualStudio.TestTools.Execution.IDataCollectorConfigurationEditor> を右クリックして、**[インターフェイスの実装]** をクリックします。 このインターフェイスに実装する必要があるメソッドがクラスに追加されます。

   2.  エディター用のユーザー コントロールに <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorConfigurationEditorAttribute> を追加して、診断データ アダプター用エディターとして識別します。このとき、**Company**、**Product**、および **Version** を診断データ アダプターに応じた情報に置き換えます。

       ```csharp
       [DataCollectorConfigurationEditorTypeUri(
           "configurationeditor://MyCompany/MyConfigEditor/1.0")]
       ```

4. 次のように 2 つのプライベート変数を追加します。

   ```csharp
   private DataCollectorSettings collectorSettings;
   private IServiceProvider ServiceProvider { get; set; }
   ```

5. 診断データ アダプター用エディターを初期化するためのコードを追加します。 settings 変数のデータを使用して、ユーザー コントロールのフィールドに既定値を追加できます。 これは、アダプターの XML 構成ファイルの `<DefaultConfiguration>` 要素に含まれるデータです。

   ```csharp
   public void Initialize(
       IServiceProvider svcProvider,
       DataCollectorSettings settings)
   {
       ServiceProvider = svcProvider;
       collectorSettings = settings;

       // Display the default file name as listed in the settings file.
       this.SuspendLayout();
       this.FileTextBox.Text = getText(collectorSettings.Configuration);
       this.ResumeLayout();
   }
   ```

6. 次のように、エディターのコントロールのデータを診断データ アダプターの API に必要な XML 形式で保存するためのコードを追加します。

   ```csharp
   public DataCollectorSettings SaveData()
   {
       collectorSettings.Configuration.InnerXml =
           String.Format(
   @"<MyCollectorName
       xmlns=""http://MyCompany/schemas/MyDiagnosticDataCollector/1.0"">
     <File FullPath=""{0}"" />
   </MyCollectorName>",
       FileTextBox.Text);
       return collectorSettings;
   }
   ```

7. 必要に応じて、`VerifyData` メソッドにデータが正しいことを検証するためのコードを追加するか、`true` が返されるようにします。

   ```csharp
   public bool VerifyData()
   {
       // Not currently verifying data
       return true;
   }
   ```

8. (省略可能) データを XML 構成ファイルで指定されている初期設定にリセットするためのコードを、`ResetToAgentDefaults()` プライベート メソッドを使用する `getText()` メソッドに追加できます。

   ```csharp
   // Reset to default value from XML configuration
   // using a custom getText() method
   public void ResetToAgentDefaults()
   {
       this.FileTextBox.Text = getText(collectorSettings.DefaultConfiguration);
   }

   // Local method to read the configuration settings
   private string getText(XmlElement element)
   {
       // Setup namespace manager with our namespace
       XmlNamespaceManager nsmgr =
           new XmlNamespaceManager(
               element.OwnerDocument.NameTable);

       // Find all the "File" elements under our configuration
       XmlNodeList files = element.SelectNodes("//ns:MyCollectorName/ns:File", nsmgr);

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
   ```

9. ソリューションをビルドします。 診断データ アダプターのアセンブリおよび XML 構成ファイル (`<diagnostic data adapter name>.dll.config`) を、*%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\PrivateAssemblies\DataCollectors* にコピーします (この場所はインストール ディレクトリによって変わります)。

    > [!NOTE]
    > 構成エディターは、診断データ アダプターとは異なるプロジェクトおよびアセンブリに配置することも、同じアセンブリに配置することもできます。

10. テストで診断データ アダプターを使用するには、既存のテスト設定の一覧から選択するか、Microsoft Test Manager または Visual Studio で新しいテスト設定を作成してから、診断データ アダプターを選択する必要があります。

     アダプターは、テストの設定の **[データと診断]** タブに、クラスに割り当てた表示名と共に表示されます。

11. テスト設定用の診断データ アダプターを構成するには、アダプター名の横の **[構成]** をクリックします。

     カスタム エディターが表示されます。

12. 必要に応じてカスタム エディターでフィールドを編集し、**[保存]** をクリックします。

13. Microsoft Test Manager からテストを実行する場合は、テストを実行する前にこれらのテストの設定をテスト計画に割り当てるか、**[オプションを指定して実行]** コマンドを使用して、テストの設定の割り当ておよびオーバーライドを行います。 テスト設定の詳細については、「[テスト設定を使用して診断情報を収集する](../test/collect-diagnostic-information-using-test-settings.md)」を参照してください。

14. 診断データ アダプターで新しい構成エディターを使用する前に、エディターを使用する各診断データ アダプター クラスに <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorConfigurationEditorAttribute> を適用し、クライアント コンピューターでそれらを再コンパイルおよび再インストールする必要があります。 診断データ アダプターおよび構成エディターのインストール方法の詳細については、「[方法: カスタム診断データ アダプターをインストールする](../test/how-to-install-a-custom-diagnostic-data-adapter.md)」を参照してください。

15. この診断データ アダプターを選択したテストの設定を使用して、テストを実行します。

     エディターで指定したデータ ファイルがテスト結果に関連付けられます。

    テストの実行時に環境を使用するようにテストの設定を構成する方法の詳細については、[テスト中の診断データの収集 (Azure Test Plans)](/azure/devops/test/collect-diagnostic-data?view=vsts) に関するページまたは[手動テストでの診断データの収集 (Azure Test Plans)](/azure/devops/test/mtm/collect-more-diagnostic-data-in-manual-tests?view=vsts)に関するページを参照してください。

## <a name="see-also"></a>関連項目

- <xref:Microsoft.VisualStudio.TestTools.Execution.IDataCollectorConfigurationEditor>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorConfigurationEditorAttribute>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorConfigurationEditorAttribute>
- [診断データ アダプターを作成してカスタム データを収集する、またはテスト コンピューターに影響を与える](../test/create-a-diagnostic-data-adapter-to-collect-custom-data-or-affect-a-test-machine.md)
- [テスト設定を使用して診断情報を収集する](../test/collect-diagnostic-information-using-test-settings.md)
- [診断データ アダプター作成用のサンプル プロジェクト](../test/sample-project-for-creating-a-diagnostic-data-adapter.md)