---
title: Visual Studio での Azure クラウド サービスのロールの構成 |Microsoft Docs
description: 設定して、Visual Studio を使用して Azure クラウド サービスの役割を構成する方法について説明します。
author: ghogen
manager: douge
assetId: d397ef87-64e5-401a-aad5-7f83f1022e16
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/21/2017
ms.author: ghogen
ms.openlocfilehash: ce2259debb55c4792c2998f0e67df69dbc8cb7f9
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/05/2018
ms.locfileid: "51003079"
---
# <a name="configure-azure-cloud-service-roles-with-visual-studio"></a>Visual Studio で Azure クラウド サービスのロールを構成する
Azure クラウド サービスには、1 つまたは複数の worker または web ロールを持つことができます。 ロールごとに、そのロールの設定方法を定義し、そのロールの実行方法も構成する必要があります。 クラウド サービス内のロールに関する詳細については、ビデオを参照してください。 [Azure Cloud Services の概要](https://channel9.msdn.com/Series/Windows-Azure-Cloud-Services-Tutorials/Introduction-to-Windows-Azure-Cloud-Services)します。 

クラウド サービスの情報は、次のファイルに格納されます。

- **ServiceDefinition.csdef** -サービス定義ファイルは、必要なロールを含むクラウド サービス、エンドポイント、および仮想マシンのサイズのランタイム設定を定義します。 格納されているデータはいずれ`ServiceDefinition.csdef`ロールが実行されているときに変更できます。
- **ServiceConfiguration.cscfg** - サービス構成ファイルは、ロールのインスタンスの数が実行を構成し、ロールの設定の値に定義します。 格納されたデータ`ServiceConfiguration.cscfg`ロールの実行中に変更することができます。

ロールの実行方法を制御する設定に別の値を格納するには、複数のサービス構成を定義できます。 展開環境ごとに異なるサービス構成を使用できます。 たとえば、ローカル サービス構成では、ローカルの Azure ストレージ エミュレーターを使用して、クラウドで Azure storage を使用する別のサービス構成を作成するには、ストレージ アカウント接続文字列を設定することができます。

Visual Studio で Azure クラウド サービスを作成するときに 2 つのサービス構成が自動的に作成され、Azure プロジェクトに追加します。

- `ServiceConfiguration.Cloud.cscfg`
- `ServiceConfiguration.Local.cscfg`

## <a name="configure-an-azure-cloud-service"></a>Azure クラウド サービスを構成します。
次の手順で示すように、Visual Studio で、ソリューション エクスプ ローラーから Azure クラウド サービスを構成できます。

1. 作成または Visual Studio で Azure クラウド サービス プロジェクトを開きます。

1. **ソリューション エクスプ ローラー**プロジェクトを右クリックし、コンテキスト メニューから選択、**プロパティ**します。
   
    ![ソリューション エクスプ ローラーのプロジェクト コンテキスト メニュー](./media/vs-azure-tools-configure-roles-for-cloud-service/solution-explorer-project-context-menu.png)

1. プロジェクトのプロパティ ページで、選択、**開発**タブ。 

    ![プロジェクト プロパティ ページ - [開発] タブ](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-development-tab.png)

1. **サービス構成**一覧で、編集するサービスの構成の名前を選択します。 (このロールのすべてのサービス構成を変更する場合は、**すべて構成**)。
   
    > [!IMPORTANT]
    > 特定のサービス構成を選択した場合、すべての構成のみ設定するため、一部のプロパティは無効です。 これらのプロパティを編集するには、するを選択する必要があります**すべて構成**します。
    > 
    > 
   
    ![Azure クラウド サービスのサービス構成の一覧](./media/vs-azure-tools-configure-roles-for-cloud-service/cloud-service-service-configuration-property.png)

## <a name="change-the-number-of-role-instances"></a>ロール インスタンスの数を変更します。
クラウド サービスのパフォーマンスを向上させるのには、ユーザーまたは特定のロールに必要な負荷の数に基づいて、実行されているロールのインスタンスの数を変更できます。 Azure でクラウド サービスが実行されるロールのインスタンスごとに個別の仮想マシンが作成されます。 これは、このクラウド サービスのデプロイの課金に影響します。 課金の詳細については、次を参照してください。 [Microsoft Azure の課金内容](/azure/billing/billing-understand-your-bill)します。

1. 作成または Visual Studio で Azure クラウド サービス プロジェクトを開きます。

1. **ソリューション エクスプ ローラー**、プロジェクト ノードを展開します。 下、**ロール**ノード、更新、および、コンテキスト メニューから選択する役割を右クリックして**プロパティ**します。

    ![ソリューション エクスプ ローラーの Azure ロールのコンテキスト メニュー](./media/vs-azure-tools-configure-roles-for-cloud-service/solution-explorer-azure-role-context-menu.png)

1. 選択、**構成**タブ。

    ![[構成] タブ](./media/vs-azure-tools-configure-roles-for-cloud-service/role-configuration-properties-page.png)

1. **サービス構成**一覧を更新するサービスの構成を選択します。
   
    ![サービス構成の一覧](./media/vs-azure-tools-configure-roles-for-cloud-service/role-configuration-properties-page-select-configuration.png)

1. **インスタンス数**テキスト ボックスに、このロールを開始するインスタンスの数を入力します。 各インスタンスは、Azure にクラウド サービスを公開するときに、別の仮想マシンで実行されます。

    ![インスタンス数の更新](./media/vs-azure-tools-configure-roles-for-cloud-service/role-configuration-properties-page-instance-count.png)

1. Visual studio では、ツールバーで、**保存**します。

## <a name="manage-connection-strings-for-storage-accounts"></a>ストレージ アカウントの接続文字列を管理します。
追加できますが、削除、または接続文字列は、サービス構成を変更します。 たとえば、ローカル接続文字列の値を持つローカル サービス構成する可能性があります`UseDevelopmentStorage=true`します。 また Azure でストレージ アカウントを使用するクラウド サービスの構成を構成する可能性があります。

> [!WARNING]
> ストレージ アカウントの接続文字列には、Azure ストレージ アカウント キー情報を入力すると、この情報は、サービス構成ファイルにローカルに格納します。 ただし、この情報は現在ありません格納されている暗号化されたテキストとして。
> 
> 

サービス構成ごとに別の値を使用すると、異なる接続文字列を使用して、クラウド サービスまたは Azure にクラウド サービスを公開するときに、コードを変更する必要はありません。 同じ接続文字列の名前を使用するには、コード内と、値は、クラウド サービスをビルドまたは発行するときに選択したサービスの構成に基づいて異なります。

1. 作成または Visual Studio で Azure クラウド サービス プロジェクトを開きます。

1. **ソリューション エクスプ ローラー**、プロジェクト ノードを展開します。 下、**ロール**ノード、更新、および、コンテキスト メニューから選択する役割を右クリックして**プロパティ**します。

    ![ソリューション エクスプ ローラーの Azure ロールのコンテキスト メニュー](./media/vs-azure-tools-configure-roles-for-cloud-service/solution-explorer-azure-role-context-menu.png)

1. 選択、**設定**タブ。

    ![[設定] タブ](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab.png)

1. **サービス構成**一覧を更新するサービスの構成を選択します。

    ![サービス構成](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-select-configuration.png)

1. 接続文字列を追加するには、選択**設定の追加**します。

    ![接続文字列を追加します。](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-add-setting.png)

1. 新しい設定が一覧に追加されたら、必要な情報を一覧の行を更新します。

    ![新しい接続文字列](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-add-setting-new-setting.png)

    - **名前**-接続文字列を使用する名前を入力します。
    - **型**- 選択**接続文字列**ドロップダウン リストから。
    - **値**-に直接接続文字列を入力するか、**値**セル、または、省略記号 (...) で作業を選択して、**ストレージ接続文字列の作成**ダイアログ。  

1. **ストレージ接続文字列の作成**ダイアログ ボックスで、オプションを選択します**を使用して接続**します。 選択したオプションの手順に従ってください。

    - **Microsoft Azure ストレージ エミュレーター** -Azure にのみ適用されるに、残りの設定 ダイアログが無効になっている場合、このオプションを選択します。 **[OK]** を選択します。
    - **サブスクリプション**- このオプションを選択した場合、ドロップダウン リストを使用して選択し、Microsoft アカウントにサインインのいずれかまたは Microsoft アカウントを追加します。 Azure サブスクリプションとストレージ アカウントを選択します。 **[OK]** を選択します。
    - **資格情報を手動で入力された**-ストレージ アカウント名とプライマリまたはセカンダリ キーのいずれかを入力します。 オプションを選択**接続**(HTTPS は、ほとんどのシナリオの推奨が)。**[OK]** を選択します。

1. 接続文字列を削除する接続文字列を選択し、**設定の削除**します。

1. Visual studio では、ツールバーで、**保存**します。

## <a name="programmatically-access-a-connection-string"></a>接続文字列をプログラムでアクセスします。

次の手順を使用して接続文字列をプログラムでアクセスする方法を示してC#します。

1. 次の追加 using ディレクティブをC#場所の設定を使用しようとするファイル。

    ```csharp
    using Microsoft.WindowsAzure;
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.ServiceRuntime;
    ```

1. 次のコードでは、接続文字列にアクセスする方法の例を示します。 置換、 &lt;ConnectionStringName > プレース ホルダーを適切な値。 

    ```csharp
    // Setup the connection to Azure Storage
    var storageAccount = CloudStorageAccount.Parse(RoleEnvironment.GetConfigurationSettingValue("<ConnectionStringName>"));
    ```

## <a name="add-custom-settings-to-use-in-your-azure-cloud-service"></a>Azure クラウド サービスで使用するカスタム設定を追加します。
サービス構成ファイルでカスタム設定では、名前と特定のサービス構成用の文字列の値を追加できます。 この設定を使用して、クラウド サービスで設定の値を読み取って、この値を使用して、コード内のロジックを制御する機能を構成することができます。 これらのサービス構成値を変更するには、サービス パッケージまたはクラウド サービスが実行されているときに再構築する必要はありません。 コードは、設定が変更されたときの通知を確認できます。 参照してください[RoleEnvironment.Changing イベント](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleenvironment.changing.aspx)します。

追加、削除、またはサービス構成のカスタム設定を変更できます。 これらの文字列を異なるサービス構成の異なる値をたい場合があります。

サービス構成ごとに別の値を使用すると、クラウド サービスでさまざまな文字列を使用して、または Azure にクラウド サービスを公開するときに、コードを変更する必要はありません。 文字列の同じ名前を使用するには、コード内と、値は、クラウド サービスをビルドまたは発行するときに選択したサービスの構成に基づいて異なります。

1. 作成または Visual Studio で Azure クラウド サービス プロジェクトを開きます。

1. **ソリューション エクスプ ローラー**、プロジェクト ノードを展開します。 下、**ロール**ノード、更新、および、コンテキスト メニューから選択する役割を右クリックして**プロパティ**します。

    ![ソリューション エクスプ ローラーの Azure ロールのコンテキスト メニュー](./media/vs-azure-tools-configure-roles-for-cloud-service/solution-explorer-azure-role-context-menu.png)

1. 選択、**設定**タブ。

    ![[設定] タブ](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab.png)

1. **サービス構成**一覧を更新するサービスの構成を選択します。

    ![サービス構成の一覧](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-select-configuration.png)

1. カスタム設定を追加するには、次のように選択します。**設定の追加**します。

    ![カスタム設定を追加します。](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-add-setting.png)

1. 新しい設定が一覧に追加されたら、必要な情報を一覧の行を更新します。

    ![新しいカスタム設定](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-add-setting-new-setting.png)

    - **名前**-設定の名前を入力します。
    - **型**- 選択**文字列**ドロップダウン リストから。
    - **値**-設定の値を入力します。 直接値を入力するか、**値**セル、またはの値を入力する省略記号 (...) を選択、**文字列の編集**ダイアログ。  

1. カスタム設定を削除する、設定を選択し、**設定の削除**します。

1. Visual studio では、ツールバーで、**保存**します。

## <a name="programmatically-access-a-custom-settings-value"></a>カスタム設定の値をプログラムでアクセスします。
 
次の手順は、カスタム設定を使用して、プログラムでアクセスする方法を示してC#します。

1. 次の追加 using ディレクティブをC#場所の設定を使用しようとするファイル。

    ```csharp
    using Microsoft.WindowsAzure;
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.ServiceRuntime;
    ```

1. 次のコードでは、カスタム設定にアクセスする方法の例を示します。 置換、 &lt;SettingName > プレース ホルダーを適切な値。 
    
    ```csharp
    var settingValue = RoleEnvironment.GetConfigurationSettingValue("<SettingName>");
    ```

## <a name="manage-local-storage-for-each-role-instance"></a>各ロール インスタンスのローカル記憶域を管理します。
ロールのインスタンスごとに、ローカル ファイル システムの記憶域を追加することができます。 記憶域にアクセスできないことに格納されているため、データが格納されているロールの他のインスタンスまたは他のロールでのデータ。  

1. 作成または Visual Studio で Azure クラウド サービス プロジェクトを開きます。

1. **ソリューション エクスプ ローラー**、プロジェクト ノードを展開します。 下、**ロール**ノード、更新、および、コンテキスト メニューから選択する役割を右クリックして**プロパティ**します。

    ![ソリューション エクスプ ローラーの Azure ロールのコンテキスト メニュー](./media/vs-azure-tools-configure-roles-for-cloud-service/solution-explorer-azure-role-context-menu.png)

1. 選択、**ローカル ストレージ**タブ。

    ![ローカル記憶域 タブ](./media/vs-azure-tools-configure-roles-for-cloud-service/role-local-storage-tab.png)

1. **サービス構成**ボックスの一覧で、**すべての構成**が選択されているは、ローカル ストレージの設定は、すべてのサービス構成に適用します。 その他の値は、無効になっている、ページ上のすべての入力フィールドになります。 

    ![サービス構成の一覧](./media/vs-azure-tools-configure-roles-for-cloud-service/role-local-storage-tab-service-configuration.png)

1. ローカル ストレージのエントリを追加するには、選択**ローカル ストレージの追加**します。

    ![ローカル ストレージを追加します。](./media/vs-azure-tools-configure-roles-for-cloud-service/role-local-storage-tab-add-local-storage.png)

1. 新しいローカル ストレージのエントリが一覧に追加されたら、必要な情報を一覧の行を更新します。

    ![新しいローカル ストレージのエントリ](./media/vs-azure-tools-configure-roles-for-cloud-service/role-local-storage-tab-new-local-storage.png)

    - **名前**-新しいローカル ストレージに使用する名前を入力します。
    - **サイズ (MB)** -新しいローカル ストレージに必要な MB のサイズを入力します。
    - **ロールのリサイクルにクリーン**-ロールの仮想マシンがリサイクルされるときに、新しいローカル ストレージにデータを削除するには、このオプションを選択します。

1. ローカル ストレージのエントリを削除するエントリを選択し、**ローカル ストレージの削除**します。

1. Visual studio では、ツールバーで、**保存**します。

## <a name="programmatically-accessing-local-storage"></a>ローカル ストレージにプログラムでアクセスします。

このセクションでは、ローカル ストレージを使用してプログラムでアクセスする方法を示しています。C#テスト テキスト ファイルを記述して`MyLocalStorageTest.txt`します。  

### <a name="write-a-text-file-to-local-storage"></a>テキスト ファイルをローカル ストレージに書き込む

次のコードでは、テキスト ファイルをローカル ストレージに書き込む方法の例を示します。 置換、 &lt;LocalStorageName > プレース ホルダーを適切な値。 

    ```csharp
    // Retrieve an object that points to the local storage resource
    LocalResource localResource = RoleEnvironment.GetLocalResource("<LocalStorageName>");
    
    //Define the file name and path
    string[] paths = { localResource.RootPath, "MyLocalStorageTest.txt" };
    String filePath = Path.Combine(paths);
    
    using (FileStream writeStream = File.Create(filePath))
    {
        Byte[] textToWrite = new UTF8Encoding(true).GetBytes("Testing Web role storage");
        writeStream.Write(textToWrite, 0, textToWrite.Length);
    }

    ```

### <a name="find-a-file-written-to-local-storage"></a>ローカル ストレージに書き込まれるファイルを検索します。

前のセクションで、コードによって作成されたファイルを表示するには、次の手順を実行します。
    
1.  Windows 通知領域に Azure のアイコンを右クリックし、コンテキスト メニューから選択**コンピューティング エミュレーター UI**します。 

    ![Azure コンピューティング エミュレーターを表示します。](./media/vs-azure-tools-configure-roles-for-cloud-service/show-compute-emulator.png)

1. Web ロールを選択します。

    ![Azure コンピューティング エミュレーター](./media/vs-azure-tools-configure-roles-for-cloud-service/compute-emulator.png)

1. **Microsoft Azure コンピューティング エミュレーター**メニューの **ツール** > **ローカル ストアを開く**します。

    ![ローカル ストアを開く メニュー項目](./media/vs-azure-tools-configure-roles-for-cloud-service/compute-emulator-open-local-store-menu.png)

1. Windows エクスプ ローラー ウィンドウが開いたら、次のように入力してください ' 'mylocalstoragetest.txt''」に、**検索**テキスト ボックス、および選択 **」と入力**検索を開始します。 

## <a name="next-steps"></a>次の手順
詳細については、Visual Studio での Azure プロジェクトを読み取るして[Azure プロジェクトの構成](vs-azure-tools-configuring-an-azure-project.md)します。 詳細については、クラウド サービスのスキーマの読み取りして[スキーマ リファレンス](https://msdn.microsoft.com/library/azure/dd179398)します。

