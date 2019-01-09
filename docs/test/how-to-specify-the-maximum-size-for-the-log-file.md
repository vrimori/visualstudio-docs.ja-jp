---
title: ロード テストのログ ファイルのサイズ
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, logging
ms.assetid: 417059bf-37ae-4e7a-b9b0-29bd71f1414f
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.openlocfilehash: 69078569f59612f5335266784d71c5003aad5f5d
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53902965"
---
# <a name="how-to-specify-the-maximum-size-for-the-log-file-for-load-tests"></a>方法: ロード テスト用ログ ファイルの最大サイズを指定する

既定では、ロード テストで使用されるログ ファイルの最大サイズは 20 MB に設定されています。 コントローラー サービスに関連付けられている構成ファイルを編集することによって、この値を変更できます。

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="specify-the-maximum-log-file-size-for-load-test"></a>ロード テスト用ログ ファイルの最大サイズの指定

1.  *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\QTCcontroller.exe.config* にある XML 構成ファイル *QTCcontroller.exe.config* を開きます。

2.  `<appSettings>` タグで `<add key="LogSizeLimitInMegs" value="20"/>` エントリを見つけます。

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
- [テスト コントローラーおよびテスト エージェント用のポートの構成](../test/configure-ports-for-test-controllers-and-test-agents.md)