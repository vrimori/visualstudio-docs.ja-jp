---
title: "ビルドまたはリリース管理を使用したテストの自動化 | Microsoft Docs"
ms.custom: 
ms.date: 05/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: automated testing, lab management, test lab
ms.assetid: F34B0D19-B430-4C01-B402-62A861007E71
caps.latest.revision: "56"
ms.author: douge
manager: douge
ms.workload: multiple
ms.openlocfilehash: d103e74c0f6cf40bfd0e6dc26dd5777c6fe11f2f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="use-build-and-release-management-instead-of-lab-management-for-automated-testing"></a>テストの自動化に、Lab Management ではなくビルドとリリース管理を使用します。

このトピックでは、テストの自動化または、ビルド、配置、テストの自動化に Microsoft Test Manager (MTM) と Lab Management を使用している場合、Team Foundation Server (TFS) および Visual Studio Team Services の[ビルドとリリース](https://www.visualstudio.com/team-services/continuous-integration/)機能を使用して同じ目的を達成する方法を説明します。

* [ビルド、配置、テストの自動化](#bdtautomation)

* [SCVMM 環境のセルフ サービスの管理](#managescvmm)

ビルドとリリース管理では、ネットワークが分離された SCVMM 環境をセルフ サービスで作成することをサポートしていません。また、将来これを提供する予定もありません。 ただし、[提案できる代替手段](#isolatedenvir)がいくつかあります。

<a name="bdtautomation"></a>
## <a name="build-deploy-test-automation"></a>ビルド、配置、テストの自動化

MTM と Lab Management は、アプリケーションのビルド、配置、テストの自動化に XAML のビルド定義に依存しています。
XAML ビルドは、目的の達成に、ラボ環境、テスト スイート、テストの設定など MTM で作成されたさまざまな構造および、ビルド コントローラー、ビルド エージェント、テスト コントローラー、テスト エージェントなどのさまざまなインフラストラクチャ コンポーネントに依存しています。 TFS と Team Services でビルドまたはリリース管理を使用すると、同じことを少ない手順で行うことができます。

| 手順 | XAML ビルドを使用する場合 | ビルドまたはリリース管理を使用する場合 |
|-------|----------------------|-----------------|
| ビルドを展開してテストを実行するマシンを特定します。 | それらのマシンの MTM に標準のラボ環境を作成します。 | N/A |
| 実行するテストを特定します。 | MTM にテスト スイートを作成し、テスト ケースを作成し、各テスト ケースと自動化を関連付けます。 テストを実行するラボ環境のマシンのロールを指定し、MTM でテスト設定を作成します。 | テスト計画でテストを管理する計画である場合、MTM に同じように自動化されたテスト スイートを作成します。 または、ビルドで生成されたテスト バイナリから直接テストを実行する場合は、これを省略することが可能です。 いずれの場合もテスト設定を作成する必要はありません。 |
| 配置とテストを自動化します。 | LabDefaultTemplate.*.xaml を使用し、XAML ビルド定義を作成します。 ビルド定義に、ビルド、テスト スイートおよびラボ環境を指定します。 | 1 つの環境の[ビルド定義またはリリース定義](https://www.visualstudio.com/team-services/continuous-integration/)を作成します。 コマンド ライン タスクを使用して (XAML ビルド定義から) 同じ配置スクリプトを実行し、Test Agent の配置と機能テストの実行タスクを使用して自動化されたテストを実行します。 これらのタスクにマシンの一覧とその資格情報を入力し指定します。 |

このシナリオでビルドまたはリリース管理を使用する利点は次のとおりです。

* ビルド コントローラーまたはテスト コントローラーが不要です。
* テスト エージェントはビルドまたはリリースの一部としてタスクでインストールされます。
* 配置の手順を簡単にカスタマイズできます。 1 つのスクリプトの使用のみに限定されなくなります。 この製品および Visual Studio Marketplace で使用可能な多数のタスクも利用できます。
* テスト スイートを維持する必要がありません。 バイナリから直接テストを実行できます。
* 各ビルドまたはリリース内で実行されたテストのより充実したインライン レポートを得ることができます。
* 各環境に現在配置され、テストされている資産 (リリース、ビルド、作業項目、コミット) を追跡できます。
* 自動化をカスタマイズして拡張し、複数のテスト環境や運用環境にも簡単に展開できるようになります。
* 自動化は、チェックインやコミットがあった場合、または特定の時刻に毎日行われるようスケジュールできます。

<a name="managescvmm"></a>
## <a name="self-service-management-of-scvmm-environments"></a>SCVMM 環境のセルフ サービスの管理

[Microsoft Test Manager のラボ センター](https://msdn.microsoft.com/library/dd997438.aspx)では、環境テンプレートのライブラリを管理する機能をサポートしたり、[SCVMM サーバー](https://technet.microsoft.com/system-center-docs/vmm/vmm)を使用したオンデマンドでの環境のプロビジョニングをサポートしています。

ラボ センターのセルフ サービス プロビジョニング機能には、次の 2 つの明確な目標があります。

* 簡単にインフラストラクチャを管理できるようにします。 VM と環境テンプレートを管理し、環境の個々のクローンを分離するプライベート ネットワークを自動的に作成することがインフラストラクチャの管理の例です。

* チームでテストと配置を行っている場合、より単純に仮想マシンが使えるようになります。 同じチーム プロジェクト セキュリティ モデルでラボ環境にアクセスできるようにすることと、テスト シナリオでそれらの仮想マシンを統合して使用できるようにすることが単純化の例です。

ただし、[Microsoft Azure](https://azure.microsoft.com/) や [Microsoft Azure Stack](https://azure.microsoft.com/overview/azure-stack/) などのより充実したパブリック クラウドおよびプライベート クラウド システムの進化のため、TFS 2017 以降のインフラストラクチャの管理機能には進展がありません。 代わりに、それらのクラウド インフラストラクチャで管理されるリソースを使いやすくする取り組みは継続されています。

次の表では、ラボ センターを使用して実行する一般的なアクティビティと、それを (インフラストラクチャを管理するアクティビティの場合) SCVMM または Azure で、または (テストおよび配置アクティビティの場合) TFS と Team Services で実行する方法をまとめています。

| 手順 | ラボ センターを使用する場合 | ビルドまたはリリース管理を使用する場合 |
|-------|----------------------|-----------------|
| 環境テンプレートのライブラリを管理します。 | ラボ環境を作成します。 仮想マシンに必要なソフトウェアをインストールします。 Sysprep を実行し、ライブラリに環境をテンプレートとして格納します。 | SCVMM 管理コンソールを直接使用して、バーチャル マシン テンプレートまたはサービス テンプレートのいずれかを作成および管理します。 Azure を使用する場合、[Azure Marketplace](https://azure.microsoft.com/marketplace/) から定義済みの [Azure Resource Manager テンプレート](https://azure.microsoft.com/documentation/templates/)または [Azure クイック スタート テンプレート](https://azure.microsoft.com/documentation/templates/)を 1 つを選択します。 |
| ラボ環境を作成します。 | ライブラリで環境テンプレートを選択し、それを配置します。 必要なパラメーターを入力し、仮想マシンの構成をカスタマイズします。 | SCVMM 管理コンソールを使用すると、テンプレートから VM またはサービス インスタンスを直接作成できます。 リソースを作成するには、Azure Portal を直接使用します。 または、環境のリリース定義を作成します。 [SCVMM Integration の拡張機能](https://marketplace.visualstudio.com/items?itemname=ms-vscs-rm.scvmmapp)の Azure のタスクを使用し、新しい仮想マシンを作成します。 この定義の新しいリリースの作成は、ラボ センターで新しい環境を作成することと同じです。 |
| マシンに接続します。 | 環境ビューアーでラボ環境を開きます。 | 仮想マシンに接続するために、SCVMM 管理コンソールを直接使用します。 または、仮想マシンの IP アドレスまたは DNS 名を使用して、リモート デスクトップ セッションを開きます。 |
| 環境のチェックポイントを取得するか、クリーンなチェックポイントに環境を復元します。 | 環境ビューアーでラボ環境を開きます。 チェックポイントを取得するまたは前のチェックポイントに復元するオプションを選択します。 | 仮想マシンでこれらの操作を実行するために、直接 SCVMM 管理コンソールを使用します。 または、これらの手順をより大規模な自動化の一環として実行するには、リリース定義の環境の一部として [SCVMM Integration 拡張機能](https://marketplace.visualstudio.com/items?itemname=ms-vscs-rm.scvmmapp)からチェックポイント タスクを含めます。 |

<a name="isolatedenvir"></a>
## <a name="self-service-creation-of-network-isolated-environments"></a>ネットワーク分離環境のセルフサービスでの作成

ネットワークが分離されたラボ環境とは、ネットワークの競合を引き起こすことがなく安全に複製できる SCVMM 仮想マシンのグループです。 これは、MTM で、一連のネットワーク インターフェイス カードを使用してプライベート ネットワークに仮想マシンを構成した、および別の一連のネットワーク インターフェイス カードを使用してパブリック ネットワークに仮想マシンを構成した一連の手順で行われました。

[Microsoft Azure](https://azure.microsoft.com/) や [Microsoft Azure Stack](https://azure.microsoft.com/overview/azure-stack/) などのより充実したパブリックおよびプライベート クラウド管理ツールの進化により、同様な機能が直接クラウド管理ツールでできるようになっています。 ビルドとリリース管理で、これを実現する同じ方法はありません。

ネットワークを分離する必要がある場合、次の代替手段の使用を検討してください。

* 複数のクローンの構成を簡単にすることが、ネットワークを分離する動機の 1 つでした。 各クローンは、元の完全なレプリカであり、コンピューター名と構成設定が同一であるため新しい環境を簡単に設定できます。 ただし、この同じ利点は、アプリケーションの最終的な配置方法が同じでないため (たとえば、実稼働の場合など) 以降のライフサイクルで問題となる場合があります。 **代わりに**実稼働環境を設定するのと同じ方法で新しい環境を設定することを検討し、ネットワークは分離しないでください。

* テストには、[Microsoft Azure](https://azure.microsoft.com/) などのパブリック クラウド インフラストラクチャを使用してください。 プロキシまたは jumpbox のみでパブリック ネットワークに公開されている、プライベート ネットワークで接続される仮想マシンのグループを設定するには、[Azure Marketplace](https://azure.microsoft.com/marketplace/) の [Azure Resource Manager テンプレート](https://azure.microsoft.com/documentation/templates/)または[Azure クイック スタート テンプレート](https://azure.microsoft.com/documentation/templates/)を使用します。
