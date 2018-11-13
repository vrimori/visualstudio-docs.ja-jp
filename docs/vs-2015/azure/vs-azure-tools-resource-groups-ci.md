---
title: Azure リソース グループ プロジェクトを使用した Azure DevOps サービスの継続的インテグレーション |Microsoft Docs
description: Visual Studio で Azure リソース グループ デプロイ プロジェクトを使用して Azure DevOps サービスの継続的インテグレーションを設定する方法について説明します。
author: mlearned
manager: douge
ms.assetid: b81c172a-be87-4adc-861e-d20b94be9e38
ms.service: azure-resource-manager
ms.topic: article
ms.workload: azure-vs
ms.date: 08/01/2016
ms.author: mlearned
ms.openlocfilehash: f6404b15e8a7cd3f95ac63bbae6076ef62fcff06
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/05/2018
ms.locfileid: "51003009"
---
# <a name="continuous-integration-in-azure-devops-services-using-azure-resource-group-deployment-projects"></a>Azure リソース グループ デプロイ プロジェクトを使用して Azure DevOps サービスでの継続的インテグレーション
Azure テンプレートをデプロイするさまざまな段階にタスクを実行する: ビルド、テストでは、Azure へのコピー (「ステージング」とも呼ばれます) とテンプレートをデプロイします。 Azure DevOps サービス テンプレートをデプロイする 2 つのさまざまな方法はあります。 両方の方法は同じ結果を提供、そのため、ワークフローに最適なものを選択します。

1. Azure リソース グループ デプロイ プロジェクト (Deploy-azureresourcegroup.ps1) に含まれている PowerShell スクリプトを実行するビルド パイプラインを 1 つのステップを追加します。 このスクリプトでは、成果物をコピーし、テンプレートをデプロイします。
2. 複数の Azure DevOps サービス ビルド ステップ、タスクを実行するそれぞれ追加します。

この記事では、両方のオプションを示します。 最初のオプションでは、Visual Studio で開発者とライフ サイクル全体で一貫性が確保される同じスクリプトを使用する利点があります。 2 番目のオプションは、組み込みのスクリプトに代わる便利な方法を提供します。 どちらの手順では、Azure DevOps サービスにチェックイン Visual Studio デプロイメント プロジェクトが既にあるとします。

## <a name="copy-artifacts-to-azure"></a>成果物を Azure にコピーします。
シナリオに関係なく、テンプレートのデプロイのために必要なすべてのアイテムがある場合をする必要があります Azure Resource Manager アクセス権を付与します。 これらの成果物のファイルを含めることができます。

* 入れ子になったテンプレート
* 構成スクリプトと DSC スクリプト
* アプリケーション バイナリ

### <a name="nested-templates-and-configuration-scripts"></a>入れ子になったテンプレートと構成スクリプト
Visual Studio によって提供されているテンプレートを使用する場合 (または Visual Studio のスニペットでビルドされた)、PowerShell スクリプトはアーティファクトをステージングするだけでなく、さまざまなデプロイメントのリソースに対する URI もパラメーター化します。 スクリプトは、アーティファクトを Azure でセキュリティで保護されたコンテナーにコピー、そのコンテナーの SaS トークンを作成し、テンプレート デプロイメントにその情報を渡します。 参照してください[テンプレートのデプロイを作成](https://msdn.microsoft.com/library/azure/dn790564.aspx)を入れ子になったテンプレートの詳細を参照してください。  タスクでは、Azure DevOps サービスを使用する場合は、テンプレートのデプロイメント適切なタスクを選択し、必要に応じて、パラメーター値を渡すステージング手順からテンプレートのデプロイメントにする必要があります。

## <a name="set-up-continuous-deployment-in-azure-pipelines"></a>パイプラインを Azure での継続的なデプロイを設定します。
パイプラインを Azure での PowerShell スクリプトを呼び出すには、ビルド パイプラインを更新する必要があります。 簡単に言うと手順は次のとおりです。 

1. ビルド パイプラインを編集します。
2. Azure のパイプラインで Azure 認証を設定します。
3. Azure リソース グループ デプロイメント プロジェクト内の PowerShell スクリプトを参照する Azure PowerShell のビルド ステップを追加します。
4. 値を設定、 *- ArtifactsStagingDirectory* Azure パイプラインでビルドされたプロジェクトを使用するパラメーター。

### <a name="detailed-walkthrough-for-option-1"></a>オプション 1 の詳細なチュートリアル
次の手順では、プロジェクトの PowerShell スクリプトを実行する 1 つのタスクを使用して Azure DevOps サービスで継続的なデプロイを構成するための手順を説明します。 

1. Azure DevOps サービス ビルド パイプラインを編集し、Azure PowerShell のビルド ステップを追加します。 ビルド パイプラインを選択、**パイプラインを構築**カテゴリ選択し、**編集**リンク。
   
   ![ビルド パイプラインを編集します。][0]
2. 新しい追加**Azure PowerShell**ビルド パイプラインのステップをビルドし、、**ビルド ステップの追加.** を追加します。
   
   ![ビルド ステップを追加します。][1]
3. 選択、**配置タスク**カテゴリを選択、 **Azure PowerShell**タスクを選び、その**追加**ボタンをクリックします。
   
   ![タスクを追加します。][2]
4. 選択、 **Azure PowerShell**ビルド ステップとその値を入力します。
   
   1. Azure DevOps サービスに追加された Azure サービス エンドポイントは、既にある場合でサブスクリプションを選択、 **Azure サブスクリプション**ドロップダウン リスト ボックスと、次のセクションにスキップします。 
      
      Azure DevOps サービスで Azure サービス エンドポイントを持っていない場合は、1 つ追加する必要があります。 ここでは、プロセスを移動します。 Azure アカウント (Hotmail など) の Microsoft アカウントを使用する場合は、サービス プリンシパルの認証を取得する次の手順を行う必要があります。

   2. 選択、**管理**リンクの横に、 **Azure サブスクリプション**ドロップダウン リスト ボックス。
      
      ![Azure サブスクリプションを管理します。][3]
   3. 選択**Azure**で、**新しいサービス エンドポイント**ドロップダウン リスト ボックス。
      
      ![新しいサービス エンドポイント][4]
   4. **Azure サブスクリプションの追加**ダイアログ ボックスで、**サービス プリンシパル**オプション。
      
      ![サービス プリンシパル オプション][5]
   5. Azure サブスクリプション情報を追加、 **Azure サブスクリプションの追加** ダイアログ ボックス。 次の項目を指定する必要があります。
      
      * サブスクリプション Id
      * サブスクリプション名
      * サービス プリンシパル Id
      * サービス プリンシパル キー
      * テナント Id
   6. 任意の名前を追加、**サブスクリプション**名 ボックスにします。 この値が入力されます後で、 **Azure サブスクリプション**Azure DevOps サービスでのドロップダウン リスト。 

   7. Azure サブスクリプション ID がわからない場合は、それを取得する次のコマンドのいずれかを使用できます。
      
      PowerShell スクリプトでは、次のコマンドを使用します。
      
      `Get-AzureRmSubscription`
      
      Azure cli では、次のコマンドを使用します。
      
      `azure account show`
   8. サービス プリンシパルの ID、サービス プリンシパル キー、およびテナント ID、次の手順を取得する[作成の Active Directory のアプリケーションとサービス プリンシパルをポータルを使用して](/azure/azure-resource-manager/resource-group-create-service-principal-portal)または[azure サービス プリンシパルの認証Resource Manager](/azure/azure-resource-manager/resource-group-authenticate-service-principal)します。
   9. サービス プリンシパルの ID、サービス プリンシパル キー、およびテナント ID 値を追加、 **Azure サブスクリプションの追加** ダイアログ ボックスをクリックして、 **OK**ボタン。
      
      使用して、Azure PowerShell スクリプトを実行する有効なサービス プリンシパルがあるようになりました。
5. ビルド パイプラインを編集し、選択、 **Azure PowerShell**ビルド ステップ。 サブスクリプションを選択、 **Azure サブスクリプション**ドロップダウン リスト ボックス。 (サブスクリプションが表示されない場合、**更新**ボタンを次に、**管理**リンクします)。 
   
   ![Azure PowerShell のビルド タスクを構成します。][8]
6. Deploy-azureresourcegroup.ps1 の PowerShell スクリプトへのパスを提供します。 これを行うに横に、省略記号 (...) ボタンを選択、**スクリプト パス**ボックスで、移動の Deploy-azureresourcegroup.ps1 PowerShell スクリプトを作成、**スクリプト**プロジェクトのフォルダーを選択し、し、選択、 **OK**ボタンをクリックします。    
   
   ![スクリプトへのパスを選択します。][9]
7. スクリプトを選択すると後のパスを更新、スクリプト、Build.StagingDirectory から実行できるため、(同じディレクトリを*ArtifactsLocation*に設定されている)。 "$(Build.stagingdirectory)/"をスクリプトのパスの先頭を追加することでこれを行います。
   
    ![スクリプトへのパスを編集します。][10]
8. **スクリプトの引数**ボックスに、(1 行) で、次のパラメーターを入力します。 Visual Studio でスクリプトを実行すると、VS でのパラメーターを使用する方法を確認できます、**出力**ウィンドウ。 この操作は、ビルド ステップでパラメーター値を設定するための開始点として使用できます。
   
   | パラメーター | 説明 |
   | --- | --- |
   | -ResourceGroupLocation |リソース グループがあるように、geo ロケーション値**eastus**または **'East US'** します。 (一重引用符を追加、名前にスペースがある場合。)参照してください[Azure リージョン](https://azure.microsoft.com/regions/)詳細についてはします。 |
   | -ResourceGroupName |この展開に使用されるリソース グループの名前。 |
   | -UploadArtifacts |このパラメーターは、指定されている場合を成果物をローカル システムから Azure にアップロードする必要があります。 のみ、テンプレートのデプロイ (の構成スクリプトを入れ子になったテンプレートなど) の PowerShell スクリプトを使用してステージングする追加のアーティファクトが必要な場合は、このスイッチを設定する必要があります。 |
   | -StorageAccountName |このデプロイ段階の成果物を使用するストレージ アカウントの名前。 このパラメーターはデプロイメントのアーティファクトをステージングする場合にのみ使用します。 このパラメーターは、指定した場合、スクリプトが以前のデプロイ中に 1 つを作成しない場合に、新しいストレージ アカウントが作成されます。 パラメーターが指定されている場合、ストレージ アカウントが既に存在する必要があります。 |
   | -StorageAccountResourceGroupName |ストレージ アカウントに関連付けられているリソース グループの名前。 このパラメーターは、StorageAccountName パラメーターの値を指定する場合にのみ必要です。 |
   | -Templatefile |Azure リソース グループ デプロイ プロジェクトのテンプレート ファイルへのパス。 柔軟性を向上させるため、絶対パスではなく、PowerShell スクリプトの位置を基準にするこのパラメーターのパスを使用します。 |
   | -TemplateParametersFile |Azure リソース グループ デプロイメント プロジェクト内のパラメーター ファイルへのパス。 柔軟性を向上させるため、絶対パスではなく、PowerShell スクリプトの位置を基準にするこのパラメーターのパスを使用します。 |
   | -ArtifactStagingDirectory |このパラメーターには、PowerShell スクリプトから、プロジェクトのバイナリ ファイルのコピー先となるフォルダーを知ることができます。 この値は、PowerShell スクリプトによって使用される既定値をオーバーライドします。 Azure DevOps サービスを使用して、値に設定 - ArtifactStagingDirectory $(Build.StagingDirectory)。 |
   
   (読みやすくするための別の行) のスクリプト引数の例を次に示します。
   
   ```    
   -ResourceGroupName 'MyGroup' -ResourceGroupLocation 'eastus' -TemplateFile '..\templates\azuredeploy.json' 
   -TemplateParametersFile '..\templates\azuredeploy.parameters.json' -UploadArtifacts -StorageAccountName 'mystorageacct' 
   –StorageAccountResourceGroupName 'Default-Storage-EastUS' -ArtifactStagingDirectory '$(Build.StagingDirectory)'    
   ```
   
   操作を完了するときに、**スクリプトの引数**ボックスは、次の一覧をようになります。
   
   ![スクリプトの引数][11]
9. Azure PowerShell のビルド ステップに必要なすべての項目を追加した後は、選択、**キュー**ビルド プロジェクトをビルドするボタン。 **ビルド**画面には、PowerShell スクリプトからの出力が表示されます。

### <a name="detailed-walkthrough-for-option-2"></a>オプション 2 の詳細なチュートリアル
次の手順には、組み込みのタスクを使用して Azure DevOps サービスで継続的なデプロイを構成するために必要な手順について説明します。

1. 2 つの新しいビルド ステップを追加する Azure DevOps サービス ビルド パイプラインを編集します。 ビルド パイプラインを選択、**ビルド定義**カテゴリ選択し、**編集**リンク。
   
   ![ビルド定義を編集します。][12]
2. ビルド パイプラインを使用する新しいビルド ステップを追加、**ビルド ステップの追加.** を追加します。
   
   ![ビルド ステップを追加します。][13]
3. 選択、**デプロイ**タスクのカテゴリを選択、 **Azure ファイル コピー**タスクを選び、その**追加**ボタンをクリックします。
   
   ![Azure File Copy タスクを追加します。][14]
4. 選択、 **Azure リソース グループの配置**タスクを選択し、**追加**ボタンをクリックし、**閉じる**、**タスク カタログ**します。
   
   ![Azure リソース グループの配置タスクを追加します。][15]
5. 選択、 **Azure File Copy**タスクし、その値を入力します。
   
   Azure DevOps サービスに追加された Azure サービス エンドポイントは、既にある場合でサブスクリプションを選択、 **Azure サブスクリプション**ドロップダウン リスト ボックス。 サブスクリプションがないを参照してください。[オプション 1](#detailed-walkthrough-for-option-1)の Azure DevOps サービスのいずれかを設定する方法。
   
   * ソース - 入力 **$(Build.StagingDirectory)**
   * Azure 接続の種類の選択**Azure Resource Manager**
   * Azure RM サブスクリプション - サブスクリプションで使用するストレージ アカウントを選択、 **Azure サブスクリプション**ドロップダウン リスト ボックス。 サブスクリプションが表示されない場合、**更新**ボタンを次に、**管理**リンク。
   * 変換先の型の選択**Azure Blob**
   * RM ストレージ アカウント - 選択したストレージ アカウントのアーティファクトをステージングに使用するよう
   * コンテナー名 - ステージング; を使用するには、コンテナーの名前を入力します。任意の有効なコンテナー名はできますが、このビルド パイプラインに専用のいずれかを使用
   
   出力値。
   
   * ストレージ コンテナーの URI の入力**artifactsLocation**
   * ストレージ コンテナーの SAS トークンの入力**artifactsLocationSasToken**
   
   ![Azure ファイル コピー タスクを構成します。][16]
6. 選択、 **Azure リソース グループの配置**ビルド ステップとその値を入力します。
   
   * Azure 接続の種類の選択**Azure Resource Manager**
   * Azure RM サブスクリプション - デプロイメントでのサブスクリプションを選択、 **Azure サブスクリプション**ドロップダウン リスト ボックス。 これは通常、前の手順で使用される同じサブスクリプションになります
   * 操作 - select**作成または更新プログラムのリソース グループ**
   * リソース グループ - リソース グループを選択するか、展開の新しいリソース グループの名前を入力
   * 場所 - リソース グループの場所を選択します。
   * テンプレート - デプロイするテンプレートの名前とパスを入力します先頭 **$(Build.StagingDirectory)**、たとえば: **$(Build.StagingDirectory/DSC-CI/azuredeploy.json)。**
   * テンプレート パラメーターの入力を使用するパラメーターの名前とパス プリペンド **$(Build.StagingDirectory)**、たとえば: **$(Build.StagingDirectory/DSC-CI/azuredeploy.parameters.json)**
   * テンプレート パラメーターのオーバーライド - 入力またはコピーし、次のコードを貼り付けます。
     
     ```    
     -_artifactsLocation $(artifactsLocation) -_artifactsLocationSasToken (ConvertTo-SecureString -String "$(artifactsLocationSasToken)" -AsPlainText -Force)
     ```
     ![Azure リソース グループ デプロイ タスクを構成します。][17]
7. ビルド パイプラインを保存し、必要なすべての項目を追加した後**新しいビルドをキュー**上部にあります。

## <a name="next-steps"></a>次の手順
読み取り[Azure Resource Manager の概要](/azure-resource-manager/resource-group-overview.md)を Azure Resource Manager と Azure リソース グループの詳細を参照してください。

[0]: media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough1.png
[1]: media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough2.png
[2]: media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough3.png
[3]: media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough4.png
[4]: media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough5.png
[5]: media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough6.png
[8]: media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough9.png
[9]: media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough10.png
[10]: media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough11b.png
[11]: media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough12.png
[12]: media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough13.png
[13]: media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough14.png
[14]: media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough15.png
[15]: media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough16.png
[16]: media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough17.png
[17]: media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough18.png
