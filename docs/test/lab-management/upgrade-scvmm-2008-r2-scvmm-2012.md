---
title: "SCVMM 2008 R2 から SCVMM 2012 へのアップグレード | Microsoft Docs"
ms.custom: 
ms.date: 05/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Upgrade SCVMM 2008 R2 to SCVMM 2012, test lab
ms.author: gewarren
manager: ghogen
ms.workload: multiple
author: gewarren
ms.openlocfilehash: 51d907dfe25d8f27065b2a4d8bbecaa3e98e42a1
ms.sourcegitcommit: 7ae502c5767a34dc35e760ff02032f4902c7c02b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/09/2018
---
# <a name="upgrade-scvmm-2008-r2-to-scvmm-2012"></a>SCVMM 2008 R2 から SCVMM 2012 へのアップグレード

Team Foundation Server の Lab Management では SCVMM 2008 R2 と SCVMM 2012 がサポートされます。 Team Foundation Server 2013 を Team Foundation Server 2015 にアップグレードする場合、SCVMM 2008 R2 から SCVMM 2012 にアップグレードするときは、Team Foundation Server 2015 へのアップグレードが完了してから、SCVMM 2012 にアップグレードすることをお勧めします。 このトピックでは、Team Foundation Server 2015 で Lab Management を使用しているときに、SCVMM 2008 R2 を SCVMM 2012 にアップグレードする方法について説明します。
Lab Management では、SCVMM 2016 はサポート**していません**。 

**重要:** SCVMM をアップグレードするとき、ある手順を実行すると、Team Foundation Server でダウンタイムが発生します。 手順は下にあります。

## <a name="upgrading-to-scvmm-2012"></a>SCVMM 2012 へのアップグレード

1. SCVMM 2012 インストーラーを使用して、SCVMM 2008 R2 サーバーを SCVMM 2012 サーバーにアップグレードします。

1. ホストおよびライブラリ共有で SCVMM エージェントをアップグレードします。

1. SCVMM 管理コンソールを使用して、すべての SCVMM コンポーネントが動作していることを確認します。

1. SCVMM 2012 管理コンソールを、Team Foundation Server のアプリケーション層のすべてのコンピューターにインストールします。

1. **iisreset** コマンドを使用して、Team Foundation Server Web サービスを再起動します。 次に、Team Foundation Server ジョブ エージェントを再起動します。

   **注意:** この手順を実行すると、Team Foundation Server 上のサービスが中断されます。

1. 各プロジェクト コレクションのデータベースのデータとテンプレートがアップグレードされ、SCVMM との互換性が与えられます。 
   2012.

   Team Foundation Server で管理者特権でのコマンド プロンプトを開き、次のコマンドを入力します。

   **C:\\Program Files\\Microsoft Team Foundation Server 14.0\\Tools\> tfsconfig lab /upgradeSCVMM /collectionName:\***

   **upgradeSCVMM** コマンドを使用すると、SCVMM サーバーに、新しいテンプレートが、そのテンプレートを使用するすべてのチーム プロジェクトに対して作成されます。 これにより、テンプレートは、SCVMM 2012 との互換性を確保しながらアップグレードされます。その際、データが失われることはありません。 ただし、新しいテンプレートを作成すると、そのテンプレートの名前にはチーム プロジェクト名が追加されます。

   **注意:**  
   新しいテンプレート名が 64 文字を超える場合は、これにより SCVMM エラーが発生します。 このエラーを解決するには、テンプレートに短い名前を付ける必要があります。 このコマンドによってその他のエラーまたは警告が発生した場合は、次のセクションを参照して、エラーを解決してください。 エラーまたは警告が発生しなければアップグレードは完了です。これで、Lab Management で SCVMM 環境を使用できます。

## <a name="resolving-errors-and-warnings-when-using-the-upgradescvmm-command"></a>upgradeSCVMM の使用時に発生するエラーと警告の解決

**upgradeSCVMM** コマンドによってエラーや警告が発生する場合、Lab Management を使用するには、そのエラーや警告を解決してから、コマンドを再実行する必要があります。 **upgradeSCVMM** コマンドを実行すると、発生したエラーや警告に関する情報が含まれるログ ファイルが生成されます。 ログ ファイルの場所は、**upgradeSCVMM** コマンドの実行時に表示されます。

**SCVMM エラー:** SCVMM エラーに関連するエラーが発生した場合は、SCVMM ジョブの履歴を使用して、エラーに関する詳細情報を取得します。 SCVMM のエラーを解決したら、**upgradeSCVMM** コマンドを再実行します。

## <a name="see-also"></a>関連項目

* [既存の Lab Management 構成の変更](https://msdn.microsoft.com/library/ee704508%28v=vs.140%29.aspx)
