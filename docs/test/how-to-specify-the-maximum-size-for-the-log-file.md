---
title: Visual Studio でのロード テスト用ログ ファイルのサイズ | Microsoft Docs
ms.date: 10/19/2016
ms.topic: article
helpviewer_keywords:
- load tests, logging
ms.assetid: 417059bf-37ae-4e7a-b9b0-29bd71f1414f
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-test
ms.openlocfilehash: 92f9843c36889c77ff0f18e79289f9a749e879b1
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/19/2018
---
# <a name="how-to-specify-the-maximum-size-for-the-log-file-for-load-tests"></a>方法: ロード テスト用ログ ファイルの最大サイズを指定する

既定では、ロード テストで使用されるログ ファイルの最大サイズは 20 MB に設定されています。 コントローラー サービスに関連付けられている構成ファイルを編集することによって、この値を変更できます。

## <a name="specify-the-maximum-log-file-size-for-load-test"></a>ロード テスト用ログ ファイルの最大サイズの指定

1.  %ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\QTCcontroller.exe.config にある XML 構成ファイル *QTCcontroller.exe.config* を開きます。

2.  `<add key="LogSizeLimitInMegs" value="20"/>` タグで `<appSettings>` エントリを見つけます。

    ```xml
    <appSettings>
        <add key="LogSizeLimitInMegs" value="20"/>
        <add key="AgentConnectionTimeoutInSeconds" value="120"/>
        <add key="AgentSyncTimeoutInSeconds" value="300"/>
        <add key="ControllerServicePort" value="6901"/>
        <add key="ControllerUsersGroup" value="TeamTestControllerUsers"/>
        <add key="ControllerAdminsGroup" value="TeamTestControllerAdmins"/>
        <add key="CreateTraceListener" value="no"/>
      </appSettings>
    ```

3.  `value ="20"` を、ログ ファイルに指定する最大許容サイズに変更します。

    > [!NOTE]
    > "0" の値を入力すると、ログ ファイルは、使用可能なディスク容量によってのみサイズの制限を受けます。

## <a name="see-also"></a>関連項目

- [ロード テストのログ設定の変更](../test/modify-load-test-logging-settings.md)
- [Test Controller および Test Agent 用のポートの構成](../test/configure-ports-for-test-controllers-and-test-agents.md)