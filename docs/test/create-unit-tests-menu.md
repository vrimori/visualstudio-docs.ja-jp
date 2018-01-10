---
title: "[単体テストの作成] コマンドを使用した単体テスト メソッド スタブの作成 | Microsoft Docs"
ms.custom: 
ms.date: 05/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: unit testing, create unit tests
ms.author: gewarren
manager: ghogen
ms.workload: multiple
author: gewarren
ms.openlocfilehash: cf851d9fbd32bfdd07c6e1a67517ddf38784799c
ms.sourcegitcommit: 7ae502c5767a34dc35e760ff02032f4902c7c02b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/09/2018
---
# <a name="create-unit-test-method-stubs-with-the-create-unit-tests-command"></a>[単体テストの作成] コマンドを使用した単体テスト メソッド スタブの作成

Visual Studio の **[単体テストの作成]** コマンドでは、単体テスト メソッド スタブを作成する機能が提供されます。 この機能を使用することで、テスト プロジェクト、テスト クラス、および内部にあるテスト メソッド スタブの構成が容易になります。 

## <a name="availability-and-extensions"></a>可用性と拡張機能

**[単体テストの作成]** メニュー コマンドは、

* Visual Studio 2015 以降の Community、Professional、および Enterprise エディションで使用できます。

* .NET Framework を対象とする C# コードのみをサポートします。

* [拡張可能](#extend-framework)であり、MSTest、MSTest V2、NUnit、xUnit 形式でのテストの生成をサポートします。

## <a name="get-started"></a>作業開始

作業を開始するには、テストするプロジェクトのコード エディターでメソッド、型、または名前空間を選択し、ショートカット メニューを開いて、**[単体テストの作成]** を選択します。 これで、**[単体テストの作成]** ダイアログが開き、そこで新しい単体テストの作成オプションを選択できます。

![[単体テストの作成] コマンドの使用](media/createunittestcommand.png)

## <a name="setting-unit-test-traits"></a>単体テストの特徴の設定

テストの自動化プロセスの一部としてこれらのテストを実行する予定の場合は、他のテスト プロジェクト (上記ダイアログの 2 番目のオプション) でテストを作成し、単体テストに単体テストの特徴を設定することを検討してください。 そうすることで、継続的インテグレーションまたは継続的配置パイプラインの一部として、これらの特定のテストを含めたり、除外したりすることがより容易になります。 特徴は、以下に示すように、単体テストに直接メタデータを追加して設定します。 

![単体テストの特徴の設定](media/createunittest.png)

<a name="extend-framework"></a>
## <a name="using-third-party-unit-test-frameworks"></a>サード パーティの単体テスト フレームワークの使用

Visual Studio では、任意のテスト フレームワークを使用して、単体テストを簡単に作成できます。 他のテスト フレームワークをインストールして追加する場合は、**[ツール]、[拡張機能と更新プログラム]** の順に選択します。
次に、**[オンライン]**、**[Visual Studio ギャラリー]**、**[ツール]** の順に展開し、**[テスト]** を選択します。 

![サード パーティのテスト フレームワークの使用](media/createunittestfx.png)

以下のテスト フレームワークの拡張機能は Visual Studio Marketplace で入手可能です。

* [テスト ジェネレーター用 NUnit 拡張機能](https://marketplace.visualstudio.com/items?itemName=NUnitDevelopers.TestGeneratorNUnitextension)
* [テスト ジェネレーター用 xUnit.net 拡張機能](https://marketplace.visualstudio.com/items?itemName=BradWilson.xUnitnetTestExtensions)

## <a name="when-should-i-use-this-feature"></a>この機能を使用するタイミング

この機能は単体テストを作成する必要がある場合は必ず使用しますが、テスト カバレッジが非常に少ないか、存在しておらず、ドキュメントがない既存のコードをテストする場合に特に使用します。 つまり、コード指定が制限されているか存在しない場合です。 コードの監視対象動作の特徴を示す[スマート単体テスト](http://blogs.msdn.com/b/visualstudioalm/archive/2014/11/19/introducing-smart-unit-tests.aspx)に似たアプローチが効果的に実装されます。

ただし、この機能は、開発者が一部のコードを記述し、それを使用して単体テストの規範をブートストラップする場合でも同様に適用されます。 コーディングのフロー内で、開発者はコードの特定部分の (テスト クラスとテスト プロジェクトが適切な) 単体テスト メソッド スタブをすばやく作成できます。 

## <a name="more-information"></a>詳細情報

ブログ記事の「[Creating unit test method stubs with "Create Unit Tests"](https://blogs.msdn.microsoft.com/visualstudioalm/2015/03/06/creating-unit-test-method-stubs-with-create-unit-tests/)」 ("単体テストの作成" をする単体テスト メソッド スタブの作成) を参照してください。

[こちら](https://blogs.msdn.microsoft.com/visualstudioalm/tag/unit-testing/)で、さらに単体テストに関するブログ記事を参照できます。
