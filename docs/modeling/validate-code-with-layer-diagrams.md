---
title: "依存関係図をコードの検証 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dependency diagrams, validating
- validation, dependency diagrams
- validation, code
- code exploration, validating
- architecture, validating
- Visual Studio Ultimate, validating code
- validation, architecture
- validation, dependencies
- MSBuild, tasks
- MSBuild, dependency diagrams
- MSBuild, validating code
ms.assetid: 70cbe55d-4b33-4355-b0a7-88c770a6f75c
caps.latest.revision: 82
author: alexhomer1
ms.author: ahomer
manager: douge
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 831452f0c06a42550f64c84e88395ca7a1d3c85e
ms.openlocfilehash: 0c4368d0f88f6f5c508b9945abd89c5e94a53d8a
ms.lasthandoff: 02/22/2017

---
# <a name="validate-code-with-dependency-diagrams"></a>依存関係図をコードを検証します。

**最新のニュース**: を参照してください[このブログの投稿](https://blogs.msdn.microsoft.com/visualstudioalm/2016/11/30/live-dependency-validation-in-visual-studio-2017/)します。

[ビデオ: リアルタイムで、アーキテクチャの依存関係を検証します。](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4) 

## <a name="why-use-dependency-diagrams"></a>依存関係図を使用する理由

コードが設計と競合しないことを確認するには、Visual Studio での依存関係図を使用してコードを検証します。 これが次の点で役立つ場合があります。  
  
-   依存関係ダイアグラムで、コード内の依存関係との依存関係の競合を確認できます。  
  
-   提案された変更によって影響を受ける可能性がある依存関係を見つける。  
  
     たとえば、潜在的なアーキテクチャの変更を表示し、影響を受ける依存関係を表示するコードを検証するには、依存関係図を編集できます。  
  
-   コードを別の設計にリファクターまたは移行する。  
  
     コードを別のアーキテクチャに移動したときに作業が必要なコード、または依存関係を見つけます。  
  
 **Requirements**  
  
-   Visual Studio  
  
-   Team Foundation ビルド サーバーにインストールされた Visual Studio (Team Foundation ビルドを使用してコードを自動的に検証するために必要)  
  
-   依存関係図をモデリング プロジェクトのソリューションです。 この依存関係図は、検証する Visual c# .NET または Visual Basic .NET のプロジェクトの成果物にリンクする必要があります。 参照してください[コードから依存関係図を作成](../modeling/create-layer-diagrams-from-your-code.md)します。  
  
 この機能をサポートする Visual Studio のバージョンを参照してください[アーキテクチャとモデリング ツールのバージョン サポート](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)します。  
  
 Visual Studio で開いている依存関係図から手動でまたはコマンド プロンプトからコードを検証することができます。 ローカル ビルドまたは Team Foundation ビルドの実行時に、コードを自動的に検証することもできます。 参照してください[Channel 9 ビデオ: デザインと、依存関係図の使用によるアーキテクチャの検証](http://go.microsoft.com/fwlink/?LinkID=252073)します。  
  
> [!IMPORTANT]
>  Team Foundation ビルドを使用してレイヤー検証を実行する場合は、ビルド サーバーに同じバージョンの Visual Studio をインストールすることも必要です。  
  
-   [項目が検証をサポートしているかを参照してください。](#SupportsValidation)  
  
-   [その他の .NET アセンブリおよびプロジェクトの検証を含める](#IncludeReferences)  
  
-   [コードを手動で検証します。](#ValidateManually)  
  
-   [コードを自動的に検証します。](#ValidateAuto)  
  
-   [レイヤー検証に関する問題のトラブルシューティングを行う](#TroubleshootingValidation)  
  
-   [理解し、レイヤー検証エラーを解決するには](#UnderstandingValidationErrors)  

## <a name="live-dependency-validation"></a>ライブの依存関係の検証

Visual Studio のこのリリースでは、依存関係の検証が、リアルタイムで行われ、エラーは Visual Studio のエラー一覧 ウィンドウですぐに表示。

* ライブ評価は c# および Visual basic.net のサポートします。 

* ライブの依存関係の検証を使用する場合は、完全なソリューションの分析を有効にする、エラー一覧 に表示されるゴールド バーから、オプション の設定を開きます。 
 - ソリューションのアーキテクチャ上のすべての問題を表示していない場合は、永続的にこの延べ棒を無視してかまいません。
 - 完全なソリューションの分析を有効にしない場合は、編集中のファイルに対してのみ、分析が行われます。<p /> 

* ライブの検証を有効にするプロジェクトをアップグレードする場合、ダイアログ ボックスは、変換の進行状況を示します。

* ライブの依存関係の検証用のプロジェクトを更新するときに、NuGet パッケージのバージョンは、すべてのプロジェクトで同じにするのにアップグレードされ、使用中で最上位のバージョンは、です。 

* プロジェクトの更新の依存関係の新しい検証プロジェクト トリガーを追加します。 
  
##  <a name="a-namesupportsvalidationa-see-if-an-item-supports-validation"></a><a name="SupportsValidation"></a>項目が検証をサポートしているかを参照してください。  
 複数のアプリ間で共有される Web サイト、Office ドキュメント、プレーン テキスト ファイル、プロジェクトのファイルにレイヤーをリンクできますが、そのレイヤーは検証プロセスは含まれません。 個々のレイヤー間に依存関係が表示されない場合、これらのレイヤーにリンクされているプロジェクトやアセンブリへの参照については、検証エラーは表示されません。 このような参照は、コードがこれらの参照を使用している場合を除き、依存関係と見なされません。  
  
1.  図上の依存関係には、1 つまたは複数のレイヤーを選択を選択するを右クリックし、をクリックし、**リンクの表示**します。  
  
2.  **レイヤー エクスプ ローラー**を見て、**検証をサポート**列です。 値が false の場合、この項目では検証がサポートされません。  
  
##  <a name="a-nameincludereferencesa-include-other-net-assemblies-and-projects-for-validation"></a><a name="IncludeReferences"></a>その他の .NET アセンブリおよびプロジェクトの検証を含める  
 対応する .NET アセンブリまたはプロジェクトへの参照に自動的に追加の依存関係図に項目をドラッグすると、**レイヤー参照**モデリング プロジェクト内のフォルダーです。 このフォルダーには、検証時に分析されたアセンブリおよびプロジェクトへの参照が格納されます。 手動で依存関係のダイアグラムにドラッグせず、その他の .NET アセンブリおよび検証のためのプロジェクトを含めることができます。  
  
1.  **ソリューション エクスプ ローラー**、モデリング プロジェクトを右クリックし、または**レイヤー参照**フォルダー、およびクリック**参照の追加**します。  
  
2.  **参照の追加** ダイアログ ボックスでは、アセンブリまたはプロジェクトを選択し、クリックして**OK**します。  
  
##  <a name="a-namevalidatemanuallya-validate-code-manually"></a><a name="ValidateManually"></a>コードを手動で検証します。  
 ソリューション項目にリンクされている、開いている依存関係図がある場合は、実行、**検証**ダイアグラムのショートカット コマンドです。 コマンド プロンプトを使用して実行する、 **msbuild**コマンドに、 **/p:ValidateArchitecture**カスタム プロパティを設定**True**します。 たとえば、コードの変更を行う場合、依存関係の競合を早期にキャッチできるようにレイヤー検証を定期的に実行します。  
  
#### <a name="to-validate-code-from-an-open-dependency-diagram"></a>開いている依存関係図からコードを検証するには   
  
1.  図の画面を右クリックし、をクリックし、**アーキテクチャの検証**します。  
  
    > [!NOTE]
    >  既定では、**ビルド アクション**に設定されている依存関係図 (.layerdiagram) ファイルのプロパティで**検証**ダイアグラムは、検証プロセスに含まれるようにします。  
  
     **エラー一覧**ウィンドウが、発生したエラーを報告します。 検証エラーに関する詳細については、次を参照してください。[把握して解決するレイヤーの検証エラー](#UnderstandingValidationErrors)します。  
  
2.  各エラーのソースを表示するでエラーをダブルクリックして、**エラー一覧**ウィンドウです。  
  
    > [!NOTE]
    >  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] では、エラーのソースの代わりにコード マップが表示されることがあります。 これは、コードの依存関係の図で指定されていないアセンブリに依存しているかが、コードには、依存関係図で指定されている依存関係がない場合に発生します。 コード マップまたはコードをレビューし、依存関係が必要であるかどうかを検証してください。 コード マップの詳細については、次を参照してください。[ソリューション間の依存関係をマップ](../modeling/map-dependencies-across-your-solutions.md)します。  
  
3.  エラーを管理するには、次を参照してください。[検証エラーを管理する](#ManageErrors)です。  
  
#### <a name="to-validate-code-at-the-command-prompt"></a>コマンド プロンプトでコードを検証するには  
  
1.  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] のコマンド プロンプトを開きます。  
  
2.  次のいずれかを選択します。  
  
    -   ソリューションの特定のモデリング プロジェクトに対してコードを検証するには、次のカスタム プロパティを使用して [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] を実行します。  
  
        ```  
        msbuild <FilePath+ModelProjectFileName>.modelproj /p:ValidateArchitecture=true  
        ```  
  
         - または  
  
         モデリングを含むフォルダーを参照し、実行してプロジェクト (.modelproj) ファイルと依存関係図[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]次のカスタム プロパティを使用。  
  
        ```  
        msbuild /p:ValidateArchitecture=true   
        ```  
  
    -   ソリューションのすべてのモデリング プロジェクトに対してコードを検証するには、次のカスタム プロパティを使用して [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] を実行します。  
  
        ```  
        msbuild <FilePath+SolutionName>.sln /p:ValidateArchitecture=true   
        ```  
  
         - または  
  
         依存関係図が入っているモデリング プロジェクトを格納し、実行する必要がありますソリューション フォルダーを参照[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]次のカスタム プロパティを使用します。  
  
        ```  
        msbuild /p:ValidateArchitecture=true  
        ```  
  
     発生したすべてのエラーが表示されます。 詳細については[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]を参照してください[MSBuild](../msbuild/msbuild1.md)と[MSBuild タスク](../msbuild/msbuild-task.md)します。  
  
 検証エラーに関する詳細については、次を参照してください。[把握して解決するレイヤーの検証エラー](#UnderstandingValidationErrors)します。  
  
###  <a name="a-namemanageerrorsa-manage-validation-errors"></a><a name="ManageErrors"></a>検証エラーを管理します。  
 開発プロセスの実行中は、検証時に報告される一部の競合を抑制できます。 たとえば、既に解決したエラーや特定のシナリオに関連しないエラーを抑制できます。 エラーを抑制した場合は、[!INCLUDE[esprfound](../code-quality/includes/esprfound_md.md)] で作業項目をログに記録することをお勧めします。  
  
> [!WARNING]
>  作業項目を作成またはそれにリンクするには、既に TFS ソース コード管理 (SCC) に接続されている必要があります。 別の TFS SCC への接続を開こうとすると、Visual Studio が現在のソリューションを自動的に閉じます。 作業項目を作成またはそれにリンクしようとする前に、適切な SCC に接続されていることを確認してください。 Visual Studio の今後のリリースでは、SCC に接続されていないとメニュー コマンドを使用できません。  
  
##### <a name="to-create-a-work-item-for-a-validation-error"></a>検証エラーの作業項目を作成するには  
  
-   **エラー一覧**ウィンドウで、エラーを右クリックし、**作業項目の作成**、し作成する作業項目の種類をクリックします。  
  
 これらのタスクを使用して、検証エラーを管理する、**エラー一覧**ウィンドウ。  
  
|**目的**|**次の手順します。**|  
|------------|----------------------------|  
|検証中に選択したエラーを抑制する|1 つまたは複数選択したエラーを右クリックし、**検証エラーの管理**、クリックして**エラーの抑制**します。<br /><br /> 抑制されたエラーは、取り消し線付きで表示されます。 次回検証を実行したとき、これらのエラーは表示されません。<br /><br /> 抑制されたエラーは、対応する依存関係図ファイルの .suppressions ファイルで追跡されます。|  
|選択したエラーの抑制を停止する|選択した抑制されたエラーまたはエラーを右クリックし、**検証エラーの管理**、クリックして**エラーの抑制の停止**します。<br /><br /> 次回検証を実行したとき、抑制されたエラーのうち選択したものが表示されます。|  
|抑制されたエラーすべてでの復元、**エラー一覧**ウィンドウ|内を右クリック、**エラー一覧**ウィンドウで、指す**検証エラーの管理**、 をクリックし、**抑制されたエラーの表示**します。|  
|すべて抑制されたエラーを非表示にする、**エラー一覧**ウィンドウ|内を右クリック、**エラー一覧**ウィンドウで、指す**検証エラーの管理**、 をクリックし、**抑制されたエラーの非表示に**します。|  
  
##  <a name="a-namevalidateautoa-validate-code-automatically"></a><a name="ValidateAuto"></a>コードを自動的に検証します。  
 ローカル ビルドを実行するたびにレイヤー検証を実行できます。 チームで Team Foundation ビルドを使用する場合、ゲート チェックインを使用してレイヤー検証を実行できます。これは、カスタム MSBuild タスクを作成することで指定できます。また、ビルド レポートを使用して検証エラーを収集することもできます。 ゲート チェックイン ビルドを作成するを参照してください。[ゲート チェックイン ビルド プロセスを使用して変更を検証する](http://msdn.microsoft.com/Library/9cfc8b9c-1023-40fd-8ab5-1b1bd9c172ec)です。  
  
#### <a name="to-validate-code-automatically-during-a-local-build"></a>ローカル ビルド時にコードを自動的に検証するには  
  
-   テキスト エディターを使用してモデリング プロジェクト (.modelproj) ファイルを開き、次のプロパティを追加します。  
  
```  
<ValidateArchitecture>true</ValidateArchitecture>  
```  
  
 \- または  
  
1.  **ソリューション エクスプ ローラー**を依存関係ダイアグラムまたはダイアグラムを含むモデリング プロジェクトを右クリックし、をクリックし、**プロパティ**します。  
  
2.  **プロパティ**ウィンドウで、設定、モデリング プロジェクトの**アーキテクチャの検証**プロパティを**True**します。  
  
     これには、検証プロセス内のモデリング プロジェクトが含まれます。  
  
3.  **ソリューション エクスプ ローラー**検証に使用する依存関係図 (.layerdiagram) ファイルをクリックします。  
  
4.  **プロパティ**ウィンドウで、ことを確認して、図の**ビルド アクション**にプロパティが設定されている**検証**します。  
  
     これには、検証プロセスに依存関係ダイアグラムが含まれます。  
  
 エラーを管理する [エラー一覧] ウィンドウで、次を参照してください。[検証エラーの管理](#ManageErrors)します。  
  
#### <a name="to-validate-code-automatically-during-a-team-foundation-build"></a>Team Foundation ビルド時にコードを自動的に検証するには  
  
1.  **チーム エクスプ ローラー**ビルド定義をダブルクリックし、クリックして**プロセス**します。  
  
2.  **ビルド プロセス パラメーター**、展開**コンパイル**では、次を入力し、 **MSBuild 引数**パラメーター。  
  
     `/p:ValidateArchitecture=true`  
  
 検証エラーに関する詳細については、次を参照してください。[把握して解決するレイヤーの検証エラー](#UnderstandingValidationErrors)します。 [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)] の詳細については、以下のトピックを参照してください。  
  
-   [アプリケーションのビルド](http://msdn.microsoft.com/Library/a971b0f9-7c28-479d-a37b-8fd7e27ef692)  
  
-   [ビルド プロセスの既定のテンプレートを使用します。](http://msdn.microsoft.com/Library/43930b12-c21b-4599-a980-2995e3d16e31)  
  
-   [使用してビルド UpgradeTemplate.xaml に基づいている変更します。](http://msdn.microsoft.com/Library/ee1a8259-1dd1-4a10-9563-66c5446ef41c)  
  
-   [ビルド プロセス テンプレートをカスタマイズします。](http://msdn.microsoft.com/Library/b94c58f2-ae6f-4245-bedb-82cd114f6039)  
  
-   [実行中のビルドの進行状況の監視](http://msdn.microsoft.com/Library/e51e3bad-2d1d-4b7b-bfcc-c43439c6c8ef)  
  
##  <a name="a-nametroubleshootingvalidationa-troubleshoot-layer-validation-issues"></a><a name="TroubleshootingValidation"></a>レイヤー検証に関する問題のトラブルシューティングを行う  
 レイヤー検証に関する問題とその解決方法について、次の表で説明します。 これらの問題は、コードと設計の間の競合によって発生するエラーとは異なります。 これらのエラーの詳細については、次を参照してください。[把握して解決するレイヤーの検証エラー](#UnderstandingValidationErrors)します。  
  
|**問題**|**考えられる原因**|**解決方法**|  
|---------------|------------------------|--------------------|  
|検証エラーが予期したとおりに発生しない。|検証は、ソリューション エクスプ ローラーで他の依存関係図からコピーされたおよび同じモデリング プロジェクト内にある依存関係図では機能しません。 この方法では、依存関係ダイアグラムには、元の依存関係図と同じ参照が含まれています。|新しい依存関係図をモデリング プロジェクトに追加します。<br /><br /> 元の依存関係図から新しい図へ要素をコピーします。|  
  
##  <a name="a-nameunderstandingvalidationerrorsa-understanding-and-resolving-layer-validation-errors"></a><a name="UnderstandingValidationErrors"></a>把握してレイヤー検証エラーを解決します。  
 依存関係図と照らし合わせてコードを検証する場合、コードが設計と競合する場合に、検証エラーが発生します。 たとえば、次の条件のとき、検証エラーが発生する場合があります。  
  
-   成果物が不適切なレイヤーに割り当てられている。 この場合、成果物を移動します。  
  
-   クラスなどの成果物が、アーキテクチャに違反する形で別のクラスを使用している。 この場合、コードをリファクタリングして依存関係を削除します。  
  
 これらのエラーを解決するには、コードを更新して、検証時にエラーが表示されなくなるようにします。 この作業は、反復的な方法で実行します。  
  
 次のセクションでは、これらのエラーで使用される構文を示し、これらのエラーの意味を説明し、エラーを解決または管理するために実行できることを提示します。  
  
|**構文**|**説明**|  
|----------------|---------------------|  
|*ArtifactN*(*ArtifactTypeN*)|*ArtifactN*は依存関係ダイアグラム上のレイヤーに関連付けられている成果物です。<br /><br /> *ArtifactTypeN*の種類は、 *ArtifactN*など、**クラス**または**メソッド**など。<br /><br /> MySolution.MyProject.MyClass.MyMethod(Method)|  
|*NamespaceNameN*|名前空間の名前。|  
|*LayerNameN*|依存関係ダイアグラム上のレイヤーの名前。|  
|*DependencyType*|間の依存関係の種類*Artifact1*と*Artifact2*します。 たとえば、 *Artifact1*が、**呼び出し**との関係*Artifact2*します。|  
  
|**エラーの構文**|**エラーの説明**|  
|----------------------|---------------------------|  
|DV0001:**無効な依存関係**|レイヤー参照別のレイヤーにマップされているコード要素にマップされます (名前空間、型、メンバー) は、コード要素が、このレイヤーを含む依存関係の検証のダイアグラムでこれらのレイヤー間の依存関係矢印が表示されていない場合は、この問題が報告されます。 これは、依存関係の制約違反です。|  
|DV1001:**無効な名前空間の名前**|この問題は、「許可 Namespace 名」プロパティには、このコード要素が定義されている名前空間が含まれていないレイヤーに関連付けられているコード要素で報告されます。 これは、名前付けの制約違反です。 定義する要素に関連付けられた、コードのレイヤーが、名前空間のセミコロンで区切って一覧は、「許可 Namespace 名」の構文が許可されます。|  
|DV1002: **unreferenceable 名前空間への依存関係**|レイヤーに関連付けられているし、層の"Unreferenceable Namespace"プロパティで定義されている名前空間で定義されている他のコード要素を参照しているコード要素では、この問題が報告されます。 これは、名前付けの制約違反です。 このレイヤーに関連付けられているコード要素で参照しないように名前空間のセミコロンで区切った一覧として「Unreferenceable 名前空間」プロパティが定義されていることに注意してください。|  
|DV1003:**名前空間の名前を [許可しない]**|この問題は、「許可されていない Namespace 名」プロパティがこのコード要素が定義されている名前空間を含むレイヤーに関連付けられているコード要素で報告されます。 これは、名前付けの制約違反です。 このレイヤーに関連付けられている要素は定義できません、コードの名前空間のセミコロンで区切った一覧として「名前空間の名前を許可しない」プロパティが定義されていることに注意してください。|  
|DV3001:**不足しているリンク**|レイヤー '*LayerName*'へのリンク'*アーティファクト*' が見つかりません。 アセンブリ参照が存在することを確認してください。|*LayerName*検出できない成果物にリンクします。 たとえば、モデリング プロジェクトでクラスを含むアセンブリへの参照が欠落しているために、クラスへのリンクが欠落している場合があります。|  
|DV9001:**アーキテクチャの分析には、内部エラーが検出されました。**|結果が不完全である可能性があります。 詳細については、ビルド イベント ログの詳細または出力ウィンドウを参照してください。|詳細については、ビルド イベント ログまたは出力ウィンドウを参照してください。|  

 
## <a name="see-also"></a>関連項目  
 [開発中にシステムを検証します。](../modeling/validate-your-system-during-development.md)   
 [ビデオ: リアルタイムで、アーキテクチャの依存関係を検証します。](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4)   

