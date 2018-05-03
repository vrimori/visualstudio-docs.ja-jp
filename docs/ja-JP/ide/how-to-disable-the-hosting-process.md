---
title: '方法 : ホスト プロセスを無効にする'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- hosting process, disabling
- vshost.exe, disabling the hosting process
ms.assetid: 9157488d-737f-454b-8d8d-36f99de38bb0
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f7970ff97c7aec42f8798da07cf2a4a2b6c8bea8
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-disable-the-hosting-process"></a>方法 : ホスト プロセスを無効にする

ホスト プロセスが有効になっていると、特定の API の呼び出しに影響する場合があります。 影響がある場合は、正しい結果が返るようにホスト プロセスを無効にする必要があります。

## <a name="to-disable-the-hosting-process"></a>ホスト プロセスを無効にするには

1.  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] で、実行可能なプロジェクトを開きます。 実行可能ファイルを生成しないプロジェクト (クラス ライブラリやサービス プロジェクトなど) には、このオプションがありません。

2.  **[プロジェクト]** メニューの **[プロパティ]** をクリックします。

3.  **[デバッグ]** タブをクリックします。

4.  **[Visual Studio ホスティング プロセスを有効にする]** チェック ボックスをオフにします。

 ホスト プロセスが無効になると、一部のデバッグ機能が使用できなくなったり、パフォーマンスが低下したりします。 詳細については、[デバッグとホスト プロセス](../debugger/debugging-and-the-hosting-process.md)に関するページを参照してください。

 一般的に、ホスト プロセスが無効になると、次のことが起こります。

-   [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] アプリケーションのデバッグが始まるまでの時間が長くなる。

-   デザイン時の式評価が使用できなくなる。

-   部分信頼デバッグが使用できなくなる。

## <a name="see-also"></a>関連項目

- [デバッグとホスト プロセス](../debugger/debugging-and-the-hosting-process.md)
- [ホスト プロセス (vshost.exe)](../ide/hosting-process-vshost-exe.md)