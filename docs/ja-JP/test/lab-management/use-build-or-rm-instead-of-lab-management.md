---
title: Visual Studio でテストの自動化にビルドまたはリリース管理を使用する
ms.date: 03/02/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- automated testing, lab management, test lab
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 607bc4646a6bacd0ae119d07e832ffca2f279152
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="use-build-and-release-management-instead-of-lab-management-for-automated-testing"></a>テストの自動化に、Lab Management ではなくビルドとリリース管理を使用します。

このトピックでは、テストの自動化または、ビルド、配置、テストの自動化に Microsoft Test Manager (MTM) と Lab Management を使用している場合、Team Foundation Server (TFS) および Visual Studio Team Services (VSTS) の[ビルドとリリース](/vsts/build-release/)機能を使用して同じ目的を達成する方法を説明します。

## <a name="build-deploy-test-automation"></a>ビルド、配置、テストの自動化

MTM と Lab Management は、アプリケーションのビルド、配置、テストの自動化に XAML のビルド定義に依存しています。 XAML ビルドは、目的の達成に、ラボ環境、テスト スイート、テストの設定など MTM で作成されたさまざまな構造および、ビルド コントローラー、ビルド エージェント、テスト コントローラー、テスト エージェントなどのさまざまなインフラストラクチャ コンポーネントに依存しています。 TFS と Team Services でビルドまたはリリース管理を使用すると、同じことを少ない手順で行うことができます。

| 手順 | XAML ビルドを使用する場合 | ビルドまたはリリース管理を使用する場合 |
|-------|----------------------|-----------------|
| ビルドを展開してテストを実行するマシンを特定します。 | それらのマシンの MTM に標準のラボ環境を作成します。 | N/A |
| 実行するテストを特定します。 | MTM にテスト スイートを作成し、テスト ケースを作成し、各テスト ケースと自動化を関連付けます。 テストを実行するラボ環境のマシンのロールを指定し、MTM でテスト設定を作成します。 | テスト計画でテストを管理する計画である場合、MTM に同じように自動化されたテスト スイートを作成します。 または、ビルドで生成されたテスト バイナリから直接テストを実行する場合は、これを省略することが可能です。 いずれの場合もテスト設定を作成する必要はありません。 |
| 配置とテストを自動化します。 | LabDefaultTemplate.*.xaml を使用し、XAML ビルド定義を作成します。 ビルド定義に、ビルド、テスト スイートおよびラボ環境を指定します。 | 1 つの環境の[ビルド定義またはリリース定義](/vsts/build-release/)を作成します。 コマンド ライン タスクを使用して (XAML ビルド定義から) 同じ配置スクリプトを実行し、Test Agent の配置と機能テストの実行タスクを使用して自動化されたテストを実行します。 これらのタスクにマシンの一覧とその資格情報を入力し指定します。 |

このシナリオでビルドまたはリリース管理を使用する利点は次のとおりです。

* ビルド コントローラーまたはテスト コントローラーが不要です。
* テスト エージェントはビルドまたはリリースの一部としてタスクでインストールされます。
* 配置の手順を簡単にカスタマイズできます。 1 つのスクリプトの使用のみに限定されなくなります。 この製品および Visual Studio Marketplace で使用可能な多数のタスクも利用できます。
* テスト スイートを維持する必要がありません。 バイナリから直接テストを実行できます。
* 各ビルドまたはリリース内で実行されたテストのより充実したインライン レポートを得ることができます。
* 各環境に現在配置され、テストされている資産 (リリース、ビルド、作業項目、コミット) を追跡できます。
* 自動化をカスタマイズして拡張し、複数のテスト環境や運用環境にも簡単に展開できるようになります。
* 自動化は、チェックインやコミットがあった場合、または特定の時刻に毎日行われるようスケジュールできます。

## <a name="self-service-management-of-scvmm-environments"></a>SCVMM 環境のセルフ サービスの管理

[Microsoft Test Manager のテスト センター](/vsts/manual-test/mtm/guidance-mtm-usage)では、環境テンプレートのライブラリを管理する機能をサポートしたり、[SCVMM サーバー](/system-center/vmm/overview?view=sc-vmm-1801)を使用したオンデマンドでの環境のプロビジョニングをサポートしたりしています。

ラボ センターのセルフ サービス プロビジョニング機能には、次の 2 つの明確な目標があります。

* 簡単にインフラストラクチャを管理できるようにします。 VM と環境テンプレートを管理し、環境の個々のクローンを分離するプライベート ネットワークを自動的に作成することがインフラストラクチャの管理の例です。

* チームでテストと配置を行っている場合、より単純に仮想マシンが使えるようになります。 同じチーム プロジェクト セキュリティ モデルでラボ環境にアクセスできるようにすることと、テスト シナリオでそれらの仮想マシンを統合して使用できるようにすることが単純化の例です。

ただし、[Microsoft Azure](https://azure.microsoft.com/) や [Microsoft Azure Stack](https://azure.microsoft.com/overview/azure-stack/) などのより充実したパブリック クラウドおよびプライベート クラウド システムの進化のため、TFS 2017 以降のインフラストラクチャの管理機能には進展がありません。 代わりに、それらのクラウド インフラストラクチャで管理されるリソースを使いやすくする取り組みは継続されています。

次の表では、ラボ センターで実行する一般的なアクティビティと、それを (インフラストラクチャを管理するアクティビティの場合) SCVMM または Azure で、または (テストおよび配置アクティビティの場合) TFS と Team Services で実行する方法をまとめています。

| 手順 | ラボ センターを使用する場合 | ビルドまたはリリース管理を使用する場合 |
|-------|----------------------|-----------------|
| 環境テンプレートのライブラリを管理します。 | ラボ環境を作成します。 仮想マシンに必要なソフトウェアをインストールします。 Sysprep を実行し、ライブラリに環境をテンプレートとして格納します。 | SCVMM 管理コンソールを直接使用して、仮想マシン テンプレートまたはサービス テンプレートのいずれかを作成および管理します。 Azure を使用する場合は、[Azure クイックスタート テンプレート](/resources/templates/)のいずれかを選択します。 |
| ラボ環境を作成します。 | ライブラリで環境テンプレートを選択し、それを配置します。 必要なパラメーターを入力し、仮想マシンの構成をカスタマイズします。 | SCVMM 管理コンソールを使用すると、テンプレートから VM またはサービス インスタンスを直接作成できます。 リソースを作成するには、Azure Portal を直接使用します。 または、環境のリリース定義を作成します。 [SCVMM Integration の拡張機能](https://marketplace.visualstudio.com/items?itemname=ms-vscs-rm.scvmmapp)の Azure のタスクを使用し、新しい仮想マシンを作成します。 この定義の新しいリリースの作成は、ラボ センターで新しい環境を作成することと同じです。 |
| マシンに接続します。 | 環境ビューアーでラボ環境を開きます。 | 仮想マシンに接続するために、SCVMM 管理コンソールを直接使用します。 または、仮想マシンの IP アドレスまたは DNS 名を使用して、リモート デスクトップ セッションを開きます。 |
| 環境のチェックポイントを取得するか、クリーンなチェックポイントに環境を復元します。 | 環境ビューアーでラボ環境を開きます。 チェックポイントを取得するまたは前のチェックポイントに復元するオプションを選択します。 | 仮想マシンでこれらの操作を実行するために、直接 SCVMM 管理コンソールを使用します。 または、これらの手順をより大規模な自動化の一環として実行するには、リリース定義の環境の一部として [SCVMM Integration 拡張機能](https://marketplace.visualstudio.com/items?itemname=ms-vscs-rm.scvmmapp)からチェックポイント タスクを含めます。 |

## <a name="creation-of-network-isolated-environments"></a>ネットワーク分離環境の作成

ネットワークが分離されたラボ環境とは、ネットワークの競合を引き起こすことがなく安全に複製できる SCVMM 仮想マシンのグループです。 これは、MTM で、一連のネットワーク インターフェイス カードを使用してプライベート ネットワークに仮想マシンを構成した、および別の一連のネットワーク インターフェイス カードを使用してパブリック ネットワークに仮想マシンを構成した一連の手順で行われました。

ただし、VSTS と TFS を SCVMM ビルドおよび配置タスクと組み合わせて使うことで、SCVMM 環境の管理、分離仮想ネットワークのプロビジョニング、およびビルド、配置、テスト シナリオの実装を、行うことができます。 たとえば、タスクを使って次のことができます。

* チェックポイントを作成、復元、削除する
* テンプレートを使って新しい仮想マシンを作成する
* 仮想マシンを開始および停止する
* SCVMM のカスタム PowerShell スクリプトを実行する

詳細については、「[Create a virtual network isolated environment for build-deploy-test scenarios](/vsts/build-release/actions/virtual-networks/create-virtual-network)」(ビルド、配置、テスト シナリオのための仮想ネットワーク分離環境を作成する) を参照してください。