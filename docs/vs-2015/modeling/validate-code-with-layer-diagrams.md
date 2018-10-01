---
title: レイヤー図を使用したコードの検証 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- layer diagrams, validating
- validation, layer diagrams
- validation, code
- code exploration, validating
- architecture, validating
- Visual Studio Ultimate, validating code
- validation, architecture
- validation, dependencies
- MSBuild, tasks
- MSBuild, layer diagrams
- MSBuild, validating code
ms.assetid: 70cbe55d-4b33-4355-b0a7-88c770a6f75c
caps.latest.revision: 84
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: 5430d436684be0bbf50004204da8bcd6a18d9bee
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47533861"
---
# <a name="validate-code-with-layer-diagrams"></a>レイヤー図を使用したコードの検証
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[依存関係図を使用したコードの検証](https://docs.microsoft.com/visualstudio/modeling/validate-code-with-layer-diagrams)です。  
  
コードが設計と競合しないことを確認するには、Visual Studio でレイヤー図を使用してコードを検証します。 これが次の点で役立つ場合があります。  
  
-   レイヤー図のコードと依存関係で依存関係間の競合を見つける。  
  
-   提案された変更によって影響を受ける可能性がある依存関係を見つける。  
  
     たとえば、レイヤー図を編集して予測されるアーキテクチャの変更を表示した後、コードを検証して、影響を受ける依存関係を確認できます。  
  
-   コードを別の設計にリファクターまたは移行する。  
  
     コードを別のアーキテクチャに移動したときに作業が必要なコード、または依存関係を見つけます。  
  
 **必要条件**  
  
-   Visual Studio  
  
-   Team Foundation ビルド サーバーにインストールされた Visual Studio (Team Foundation ビルドを使用してコードを自動的に検証するために必要)  
  
-   レイヤー図を使用するモデリング プロジェクトが含まれたソリューション。 このレイヤー図は、検証する対象の Visual C# プロジェクトまたは Visual Basic .NET プロジェクトの成果物にリンクしている必要があります。 参照してください[コードからレイヤー図を作成する](../modeling/create-layer-diagrams-from-your-code.md)します。  
  
 この機能をサポートする Visual Studio のバージョンを確認するには、「 [アーキテクチャ ツールとモデリング ツールのバージョン サポート](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)」を参照してください。  
  
 Visual Studio で開いているレイヤー図から、またはコマンド プロンプトから、コードを手動で検証できます。 ローカル ビルドまたは Team Foundation ビルドの実行時に、コードを自動的に検証することもできます。 参照してください[Channel 9 ビデオ: デザインとレイヤー図の使用によるアーキテクチャの検証](http://go.microsoft.com/fwlink/?LinkID=252073)です。  
  
> [!IMPORTANT]
>  Team Foundation ビルドを使用してレイヤー検証を実行する場合は、ビルド サーバーに同じバージョンの Visual Studio をインストールすることも必要です。  
  
-   [項目が検証をサポートしているかを参照してください。](#SupportsValidation)  
  
-   [その他の .NET アセンブリおよび検証用のプロジェクトが含まれます](#IncludeReferences)  
  
-   [手動でコードを検証します。](#ValidateManually)  
  
-   [コードを自動的に検証します。](#ValidateAuto)  
  
-   [レイヤー検証に関する問題をトラブルシューティングします。](#TroubleshootingValidation)  
  
-   [理解し、レイヤー検証エラーを解決するには](#UnderstandingValidationErrors)  
  
##  <a name="SupportsValidation"></a> 項目が検証をサポートしているかを参照してください。  
 複数のアプリ間で共有される Web サイト、Office ドキュメント、プレーン テキスト ファイル、プロジェクトのファイルにレイヤーをリンクできますが、そのレイヤーは検証プロセスは含まれません。 個々のレイヤー間に依存関係が表示されない場合、これらのレイヤーにリンクされているプロジェクトやアセンブリへの参照については、検証エラーは表示されません。 このような参照は、コードがこれらの参照を使用している場合を除き、依存関係と見なされません。  
  
1.  レイヤー図では、1 つまたは複数のレイヤーを選択します。 で、選択を右クリックし、[] をクリックし、**ビュー リンク**します。  
  
2.  **レイヤー エクスプ ローラー**を見て、**検証をサポート**列。 値が false の場合、この項目では検証がサポートされません。  
  
##  <a name="IncludeReferences"></a> その他の .NET アセンブリおよび検証用のプロジェクトが含まれます  
 対応する .NET アセンブリまたはプロジェクトへの参照の追加は自動的にレイヤー図に項目をドラッグすると、**レイヤー参照**モデリング プロジェクト内のフォルダー。 このフォルダーには、検証時に分析されたアセンブリおよびプロジェクトへの参照が格納されます。 また、その他の検証対象の .NET アセンブリおよびプロジェクトを、手動でレイヤー図にドラッグせずに含めることもできます。  
  
1.  **ソリューション エクスプ ローラー**、モデリング プロジェクトを右クリックして、または**レイヤー参照**フォルダー、およびクリック**参照の追加**します。  
  
2.  **参照の追加** ダイアログ ボックスでは、アセンブリまたはプロジェクトを選択しをクリックして**OK**します。  
  
##  <a name="ValidateManually"></a> 手動でコードを検証します。  
 開いているレイヤー図をソリューション アイテムにリンクされているがある場合、は、実行、**検証**ダイアグラムからのショートカット コマンド。 実行するコマンド プロンプトを使用することもできます、 **msbuild**コマンドと、 **/p:ValidateArchitecture**カスタム プロパティを設定**True**します。 たとえば、コードの変更を行う場合、依存関係の競合を早期にキャッチできるようにレイヤー検証を定期的に実行します。  
  
#### <a name="to-validate-code-from-an-open-layer-diagram"></a>開かれているレイヤー図からコードを検証するには  
  
1.  ダイアグラム サーフェイスを右クリックし、**アーキテクチャの検証**です。  
  
    > [!NOTE]
    >  既定で、**ビルド アクション**、レイヤー図 (.layerdiagram) ファイルのプロパティに設定されて**検証**検証プロセスで、ダイアグラムが含まれるようにします。  
  
     **エラー一覧**ウィンドウが発生したエラーを報告します。 検証エラーに関する詳細については、次を参照してください。[を把握して解決のレイヤー検証エラー](#UnderstandingValidationErrors)します。  
  
2.  各エラーのソースを表示するでエラーをダブルクリックして、**エラー一覧**ウィンドウ。  
  
    > [!NOTE]
    >  [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] では、エラーのソースの代わりにコード マップが表示されることがあります。 これは、レイヤー図で指定されていないアセンブリ上にコードの依存関係があるか、レイヤー図で指定された依存関係がコードにない場合に起こります。 コード マップまたはコードをレビューし、依存関係が必要であるかどうかを検証してください。 コード マップの詳細については、次を参照してください。[ソリューション間の依存関係をマップする](../modeling/map-dependencies-across-your-solutions.md)します。  
  
3.  エラーを管理するには、次を参照してください。[検証エラーを管理](#ManageErrors)します。  
  
#### <a name="to-validate-code-at-the-command-prompt"></a>コマンド プロンプトでコードを検証するには  
  
1.  [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] のコマンド プロンプトを開きます。  
  
2.  次のいずれかを選択します。  
  
    -   ソリューションの特定のモデリング プロジェクトに対してコードを検証するには、次のカスタム プロパティを使用して [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] を実行します。  
  
        ```  
        msbuild <FilePath+ModelProjectFileName>.modelproj /p:ValidateArchitecture=true  
        ```  
  
         - または  
  
         モデリング プロジェクト (.modelproj) ファイルとレイヤー図が入っているフォルダーを参照し、次のカスタム プロパティを使用して [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] を実行します。  
  
        ```  
        msbuild /p:ValidateArchitecture=true   
        ```  
  
    -   ソリューションのすべてのモデリング プロジェクトに対してコードを検証するには、次のカスタム プロパティを使用して [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] を実行します。  
  
        ```  
        msbuild <FilePath+SolutionName>.sln /p:ValidateArchitecture=true   
        ```  
  
         - または  
  
         レイヤー図が入っているモデリング プロジェクトを必ず含むソリューション フォルダーを参照し、次のカスタム プロパティを使用して [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] を実行します。  
  
        ```  
        msbuild /p:ValidateArchitecture=true  
        ```  
  
     発生したすべてのエラーが表示されます。 詳細については[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]を参照してください[MSBuild](../msbuild/msbuild.md)と[MSBuild タスク](../msbuild/msbuild-task.md)します。  
  
 検証エラーに関する詳細については、次を参照してください。[を把握して解決のレイヤー検証エラー](#UnderstandingValidationErrors)します。  
  
###  <a name="ManageErrors"></a> 検証エラーを管理します。  
 開発プロセスの実行中は、検証時に報告される一部の競合を抑制できます。 たとえば、既に解決したエラーや特定のシナリオに関連しないエラーを抑制できます。 エラーを抑制した場合は、[!INCLUDE[esprfound](../includes/esprfound-md.md)] で作業項目をログに記録することをお勧めします。  
  
> [!WARNING]
>  作業項目を作成またはそれにリンクするには、既に TFS ソース コード管理 (SCC) に接続されている必要があります。 別の TFS SCC への接続を開こうとすると、Visual Studio が現在のソリューションを自動的に閉じます。 作業項目を作成またはそれにリンクしようとする前に、適切な SCC に接続されていることを確認してください。 Visual Studio の今後のリリースでは、SCC に接続されていないとメニュー コマンドを使用できません。  
  
##### <a name="to-create-a-work-item-for-a-validation-error"></a>検証エラーの作業項目を作成するには  
  
-   **エラー一覧**ウィンドウで、エラーを右クリックし、 をポイント**作業項目の作成**、しを作成する作業項目の種類をクリックします。  
  
 これらのタスクを使用して、検証エラーを管理する、**エラー一覧**ウィンドウ。  
  
|**目的**|**次の手順します。**|  
|------------|----------------------------|  
|検証中に選択したエラーを抑制する|1 つまたは複数選択したエラーを右クリックし、[**検証エラーの管理**、] をクリックし、**エラーの抑制**します。<br /><br /> 抑制されたエラーは、取り消し線付きで表示されます。 次回検証を実行したとき、これらのエラーは表示されません。<br /><br /> 抑制されたエラーは、対応するレイヤー図ファイルの .suppressions ファイルで追跡されます。|  
|選択したエラーの抑制を停止する|選択した抑制されたエラーまたはエラーを右クリックし、 をポイント**検証エラーの管理**、 をクリックし、**エラーの抑制の停止**。<br /><br /> 次回検証を実行したとき、抑制されたエラーのうち選択したものが表示されます。|  
|復元ですべての抑制されたエラー、**エラー一覧**ウィンドウ|任意の場所を右クリックし、**エラー一覧**ウィンドウで、 をポイント**検証エラーの管理**、順にクリックします**抑制されたエラーの表示**します。|  
|すべての抑制されたエラーを非表示にする、**エラー一覧**ウィンドウ|任意の場所を右クリックし、**エラー一覧**ウィンドウで、 をポイント**検証エラーの管理**、順にクリックします**抑制されたエラーの非表示にする**します。|  
  
##  <a name="ValidateAuto"></a> コードを自動的に検証します。  
 ローカル ビルドを実行するたびにレイヤー検証を実行できます。 チームで Team Foundation ビルドを使用する場合、ゲート チェックインを使用してレイヤー検証を実行できます。これは、カスタム MSBuild タスクを作成することで指定できます。また、ビルド レポートを使用して検証エラーを収集することもできます。 ゲート チェックイン ビルドを作成するを参照してください。[ゲート チェックイン ビルド プロセスを使用して変更を検証する](http://msdn.microsoft.com/library/9cfc8b9c-1023-40fd-8ab5-1b1bd9c172ec)します。  
  
#### <a name="to-validate-code-automatically-during-a-local-build"></a>ローカル ビルド時にコードを自動的に検証するには  
  
-   テキスト エディターを使用してモデリング プロジェクト (.modelproj) ファイルを開き、次のプロパティを追加します。  
  
```  
<ValidateArchitecture>true</ValidateArchitecture>  
```  
  
 \- または -  
  
1.  **ソリューション エクスプ ローラー**レイヤー図または図を含むモデリング プロジェクトを右クリックし、クリックして**プロパティ**します。  
  
2.  **プロパティ**ウィンドウで、設定、モデリング プロジェクトの**アーキテクチャの検証**プロパティを**True**します。  
  
     これには、検証プロセス内のモデリング プロジェクトが含まれます。  
  
3.  **ソリューション エクスプ ローラー**検証に使用するレイヤー図 (.layerdiagram) ファイルをクリックします。  
  
4.  **プロパティ**ウィンドウで、ことを確認します、ダイアグラムの**ビルド アクション**プロパティに設定されて**検証**です。  
  
     これには、検証プロセス内のレイヤー図が含まれます。  
  
 エラー一覧 ウィンドウでエラーを管理するには、次を参照してください。[検証エラーの管理](#ManageErrors)します。  
  
#### <a name="to-validate-code-automatically-during-a-team-foundation-build"></a>Team Foundation ビルド時にコードを自動的に検証するには  
  
1.  **チーム エクスプ ローラー**ビルドの定義をダブルクリックし、クリックして**プロセス**します。  
  
2.  **ビルド プロセス パラメーター**、展開**コンパイル**では、次を入力し、 **MSBuild 引数**パラメーター。  
  
     `/p:ValidateArchitecture=true`  
  
 検証エラーに関する詳細については、次を参照してください。[を把握して解決のレイヤー検証エラー](#UnderstandingValidationErrors)します。 [!INCLUDE[esprbuild](../includes/esprbuild-md.md)] の詳細については、以下のトピックを参照してください。  
  
-   [アプリケーションのビルド](http://msdn.microsoft.com/library/a971b0f9-7c28-479d-a37b-8fd7e27ef692)  
  
-   [既定のテンプレートを使用して、自分のビルド プロセス](http://msdn.microsoft.com/library/43930b12-c21b-4599-a980-2995e3d16e31)  
  
-   [Upgradetemplate.xaml はレガシ ビルドの変更します。](http://msdn.microsoft.com/library/ee1a8259-1dd1-4a10-9563-66c5446ef41c)  
  
-   [ビルド プロセス テンプレートをカスタマイズします。](http://msdn.microsoft.com/library/b94c58f2-ae6f-4245-bedb-82cd114f6039)  
  
-   [実行中のビルドの進行状況の監視](http://msdn.microsoft.com/library/e51e3bad-2d1d-4b7b-bfcc-c43439c6c8ef)  
  
##  <a name="TroubleshootingValidation"></a> レイヤー検証に関する問題をトラブルシューティングします。  
 レイヤー検証に関する問題とその解決方法について、次の表で説明します。 これらの問題は、コードと設計の間の競合によって発生するエラーとは異なります。 これらのエラーの詳細については、次を参照してください。[を把握して解決のレイヤー検証エラー](#UnderstandingValidationErrors)します。  
  
|**問題点**|**考えられる原因**|**解決策**|  
|---------------|------------------------|--------------------|  
|検証エラーが予期したとおりに発生しない。|検証はソリューション エクスプローラーの他のレイヤー図からコピーされたレイヤー図および同じモデリング プロジェクトのレイヤー図には機能しません。 この方法でコピーされたレイヤー図には、コピー元のレイヤー図と同じ参照が含まれます。|新しいレイヤー図をモデリング プロジェクトに追加します。<br /><br /> コピー元のレイヤー図から新しいレイヤー図へ要素をコピーします。|  
  
##  <a name="UnderstandingValidationErrors"></a> 理解とレイヤー検証エラーの解決  
 レイヤー図と照らし合わせてコードを検証すると、コードが設計と競合している場合に検証エラーが発生します。 たとえば、次の条件のとき、検証エラーが発生する場合があります。  
  
-   成果物が不適切なレイヤーに割り当てられている。 この場合、成果物を移動します。  
  
-   クラスなどの成果物が、アーキテクチャに違反する形で別のクラスを使用している。 この場合、コードをリファクタリングして依存関係を削除します。  
  
 これらのエラーを解決するには、コードを更新して、検証時にエラーが表示されなくなるようにします。 この作業は、反復的な方法で実行します。  
  
 次のセクションでは、これらのエラーで使用される構文を示し、これらのエラーの意味を説明し、エラーを解決または管理するために実行できることを提示します。  
  
|**構文**|**説明**|  
|----------------|---------------------|  
|*ArtifactN*(*ArtifactTypeN*)|*ArtifactN*がレイヤー図のレイヤーに関連付けられている成果物。<br /><br /> *ArtifactTypeN*の種類は、 *ArtifactN*などを**クラス**または**メソッド**など。<br /><br /> MySolution.MyProject.MyClass.MyMethod(Method)|  
|*NamespaceNameN*|名前空間の名前。|  
|*LayerNameN*|レイヤー図のレイヤーの名前。|  
|*DependencyType*|間の依存関係の種類*Artifact1*と*Artifact2*します。 たとえば、 *Artifact1*が、**呼び出し**と関係*Artifact2*します。|  
  
|**エラーの構文**|**エラーの説明**|  
|----------------------|---------------------------|  
|Av 0001: 無効な依存関係: *Artifact1*(*ArtifactType1*)--> *Artifact2*(*ArtifactType2*)<br /><br /> レイヤー: *LayerName1*、 *LayerName2* &#124;依存関係: *DependencyType*|*アイテム 1*で*LayerName1*依存関係のない*Artifact2*で*LayerName2*ため*LayerName1*直接の依存関係を持たない*LayerName2*します。|  
|Av 1001: 無効な Namespace:*成果物*<br /><br /> レイヤー: *LayerName* &#124; Namespace に必要な: *NamespaceName1* &#124;現在 Namespace: *NamespaceName2*|*LayerName* 、関連する成果物がする必要がありますに属していることが必要です。 *NamespaceName1*します。 *成果物*に*NamespaceName2*ではなく、 *NamespaceName1*します。|  
|AV1002: 禁止された Namespace によって異なります*Artifact1*(*ArtifactType1*) &#124; *Artifact2*(*ArtifactType2*)。<br /><br /> レイヤー: *LayerName* &#124; Namespace は禁止されています: *NamespaceName* &#124;依存関係: *DependencyType*|*LayerName*に、関連する成果物が依存する必要がありますしないことが必要です。 *NamespaceName*します。 *アイテム 1*に依存できない*Artifact2*ため*Artifact2*に*NamespaceName*します。|  
|AV1003: で禁止されている Namespace:*成果物*(*ArtifactType*)<br /><br /> レイヤー: *LayerName* &#124; Namespace は禁止されています: *NamespaceName*|*LayerName* 、関連する成果物できませんに属していることが必要です。 *NamespaceName*します。 *成果物*に属している*NamespaceName*します。|  
|Av 3001: 不足しているリンク: のレイヤー '*LayerName*'へのリンク'*成果物*' が見つかりません。 アセンブリ参照が存在することを確認してください。|*LayerName*見つけることのできない成果物へのリンク。 たとえば、モデリング プロジェクトでクラスを含むアセンブリへの参照が欠落しているために、クラスへのリンクが欠落している場合があります。|  
|AV9001: アーキテクチャの検証で内部エラーが検出されました。 結果が不完全である可能性があります。 詳細については、ビルド イベント ログの詳細または出力ウィンドウを参照してください。|詳細については、ビルド イベント ログまたは出力ウィンドウを参照してください。|  
  
## <a name="security"></a>セキュリティ  
  
## <a name="see-also"></a>関連項目  
 [開発時のシステムの検証](../modeling/validate-your-system-during-development.md)



