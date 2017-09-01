---
title: "テスト エージェントをインストールして構成する | Microsoft Docs"
ms.custom: 
ms.date: 05/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configure test agents, test lab
ms.assetid: EBAA2E04-A97A-4047-B739-8DBA7F2D5074
caps.latest.revision: 56
ms.author: douge
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 45d36934cf1c46902cac566203cddf4a118b7fe4
ms.openlocfilehash: 5d9aec436c00bc999356e402facf605c194c9d1a
ms.contentlocale: ja-jp
ms.lasthandoff: 06/02/2017

---
# <a name="install-and-configure-test-agents"></a>テスト エージェントをインストールして構成する

Visual Studio と Visual Studio Team Services または Team Foundation Server (TFS) を使用するテスト シナリオの場合、Agents for Microsoft Visual Studio は Team Services または TFS と通信してオーケストレーションを処理するため、テスト コントローラーは必要ありません。 たとえば、Team Services または TFS でビルドおよびリリース ワークフローを使用して継続的なテストを実行します。

TFS 2013 で動作するテスト エージェントまたはテスト コントローラーが必要な場合は、Agents for Microsoft Visual Studio 2013 Update 5 を使用して、テスト コントローラーを構成します。

代わりに[ビルドまたは Release Management を使用する](lab-management/use-build-or-rm-instead-of-lab-management.md)ほうが簡単であるかどうかも考慮してください。

## <a name="what-do-i-need"></a>どうしたらよいですか?

**テスト コントローラーおよびテスト エージェントはどこで取得するのですか?**

* ビルド vNext タスクを使用してテストを実行し、ローカル ディレクトリからエージェントをインストールする場合 - 

  * [Agents for Microsoft Visual Studio 2015 RTM および Update 1 をダウンロードします](http://go.microsoft.com/fwlink/p/?LinkId=619266)。 

  * [Agents for Microsoft Visual Studio 2017 および Visual Studio 2015 Update 2 をダウンロードします](https://www.visualstudio.com/downloads/download-visual-studio-vs)。左側のナビゲーション バーから **[Tools for Visual Studio 2015]** を選択し、**[Agents for Visual Studio 2015]** を選択します。

* 次の作業を行う場合は、[Agents for Microsoft Visual Studio 2013 Update 5 をダウンロードします](http://go.microsoft.com/fwlink/p/?LinkId=619264)。

  * オンプレミス リモート コンピューターを使用するロード テスト。

  * Microsoft Test Manager または MSTest とラボ環境のテスト設定を使用するリモートでの継続的なテスト。

  * TFS 2013 を使用する継続的なテスト。

これらのインストーラーは ISO ファイル (仮想 CD) として利用可能であるため、仮想マシンに簡単にインストールできます。 

[TFS、Microsoft Test Manager、テスト コント ローラー、テスト エージェントのバージョンを混用できますか?](#MixedVersions)

**テスト コントローラーとテスト エージェントをインストールする場合に必要なシステム要件は何ですか?**

| アイテム | 要件 |
| ---- | ------------ |
| **エージェント** | Windows 10<br />Windows 8、Windows 8.1<br />Windows 7 Service Pack 1<br />Windows XP Service Pack 3<br />Windows Server 2012、Windows Server 2012 R2<br />Windows Server 2008 Release 2 Service Pack 1 |
| **コントローラー** | Windows 10<br />Windows 8、Windows 8.1<br />Windows 7 Service Pack 1<br />Windows Server 2012、Windows Server 2012 R2<br />Windows Server 2008 Release 2 Service Pack 1 |
| **.NET Framework** | .NET Framework 4.5 |

## <a name="q--a"></a>Q & A

<!-- BEGINSECTION class="m-qanda" -->

<a name="MixedVersions"></a>

####<a name="q-can-i-mix-versions-of-tfs-microsoft-test-manager-the-test-controller-and-test-agent"></a>Q: TFS、Microsoft Test Manager、テスト コント ローラー、テスト エージェントのバージョンを混用できますか?

A: はい。互換性のあるサポートされている組み合わせを以下に示します。

| TFS | Microsoft Test Manager (ラボ センターを使用する場合) | コントローラー | エージェント |
| --- | -------------------------------------- | ---------- | ----- |
| 2015: 2013 からのアップグレード | 2013 | 2013 |2013 |
| 2015: 新規インストール | 2013 | 2013 | 2013 |
| 2015: 2013 からのアップグレードまたは新規インストール | 2015 | 2013 | 2013 |
| 2013 | 2015 | 2013 | 2013 |

####<a name="q-will-the-test-agent-2015-support-all-the-scenarios-supported-by-test-controller-and-test-agent-of-visual-studio-2013"></a>Q: Test Agent 2015 では、Visual Studio 2013 の Test Controller と Test Agent でサポートされるすべてのシナリオがサポートされますか?

A: すべての新しい自動テストシナリオでは Agents for Visual Studio を使用することをお勧めします。 ビルド定義でテスト エージェントの配置タスクを使用して、コンピューター上にテスト エージェントをダウンロードしてインストールすることができます。
次の表は、Agents for Visual Studio 2013 でサポートされるシナリオと、Team Foundation Server (TFS) 2015 および Team Services (TS) での代替シナリオを示しています。

| Agents for Visual Studio 2013 でサポートされるシナリオ | TFS および TS での代替シナリオ |
| --- | --- |
| Visual Studio でのビルド-配置-テスト ワークフロー | ユーザーは、TFS でのビルド、配置、およびテスト シナリオで[ビルド定義](https://www.visualstudio.com/team-services/continuous-integration/) (XAML ビルドではない) を使用できます。 |
| オンプレミス リモート コンピューターを使用するロード テスト (パフォーマンス テスト) | Test Controller/Test Agents 2013 Update 5 を使用して、オンプレミスでロード テストを実行します。 詳細については、[こちら](https://msdn.microsoft.com/en-us/library/ff400223.aspx)を参照してください。 |
| ラボ環境を使用する Microsoft Test Manager からの自動テストのリモート実行 | 現在、このシナリオに代わるものはありません。 ビルドおよびリリース定義 (XAML ビルドではない) で機能テストの実行タスクを使用して、テストをリモートで実行することをお勧めします。 |
| 開発者による Visual Studio でのリモート テストの実行 | サポート対象から除外されました。 |

<!-- ENDSECTION -->

## <a name="see-also"></a>関連項目

* [コンピューターの設定およびテストの設定を使用した診断情報の収集](https://msdn.microsoft.com/library/dd286743%28v=vs.140%29.aspx)

