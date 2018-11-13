---
title: デバッグ、公開された Azure クラウドの Visual Studio と IntelliTrace を使用してサービス |Microsoft Docs
description: Visual Studio と IntelliTrace のクラウド サービスをデバッグする方法について説明します
author: mikejo5000
manager: douge
ms.assetid: 5e6662fc-b917-43ea-bf2b-4f2fc3d213dc
ms.topic: conceptual
ms.custom: vs-azure
ms.workload: azure-vs
ms.date: 03/21/2017
ms.author: mikejo
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.openlocfilehash: 865642bb7c8e41f81ff4b44ce628082e19b63a56
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002949"
---
# <a name="debugging-a-published-azure-cloud-service-with-visual-studio-and-intellitrace"></a>Visual Studio と IntelliTrace を使用した発行済みの Azure クラウド サービスのデバッグ
Azure で実行時に、IntelliTrace を使用したロール インスタンスの広範なデバッグ情報を記録できます。 問題の原因を見つける必要がある場合は、Azure で実行されている場合に、Visual Studio からコードをステップに IntelliTrace ログを使用できます。 実際には、IntelliTrace が記録キー コードが実行され、環境のデータと、Azure アプリケーションが Azure では、クラウド サービスとして実行されていると、Visual Studio から記録されたデータを再生することができます。 

Visual Studio Enterprise がインストールされている場合に IntelliTrace と Azure アプリケーションの対象 .NET Framework 4 またはそれ以降のバージョンを使用することができます。 IntelliTrace は、Azure ロールの情報を収集します。 これらのロール用の仮想マシンは、常に 64 ビット オペレーティング システムを実行します。

代わりに、使用することができます[リモート デバッグ](http://go.microsoft.com/fwlink/p/?LinkId=623041)Azure で実行されているクラウド サービスに直接接続します。

> [!IMPORTANT]
> IntelliTrace は、デバッグ シナリオのみのためのものではおよび運用環境のデプロイは使用しない必要があります。
> 

## <a name="configure-an-azure-application-for-intellitrace"></a>IntelliTrace の Azure アプリケーションを構成します。
Azure アプリケーションで IntelliTrace を有効にするには作成する必要があり、Visual Studio Azure プロジェクトからアプリケーションを発行します。 Azure に発行する前に、Azure アプリケーションの IntelliTrace を構成する必要があります。 IntelliTrace を構成せずにアプリケーションを発行する場合は、プロジェクトを再発行する必要があります。 詳細については、次を参照してください。 [services Visual Studio を使用してプロジェクトを Azure のクラウドを発行](http://go.microsoft.com/fwlink/p/?LinkId=623012)します。

1. Azure アプリケーションをデプロイする準備ができたら、プロジェクトのビルド ターゲットに設定されていることを確認**デバッグ**します。

1. **ソリューション エクスプ ローラー**プロジェクトを右クリックし、コンテキスト メニューから選択、**発行**します。
   
1. **Azure アプリケーションの発行**ダイアログで、Azure サブスクリプションを選択し選択**次**します。

1. **設定**] ページで、[、**詳細設定**タブ。

1. オンにする、 **IntelliTrace を有効に**クラウドに発行されていると、アプリケーションの IntelliTrace ログを収集するオプション。
   
1. 基本の IntelliTrace 構成をカスタマイズするには、次のように選択します。**設定**横に**IntelliTrace を有効に**します。

    ![IntelliTrace の設定 リンク](./media/vs-azure-tools-intellitrace-debug-published-cloud-services/intellitrace-settings-link.png)
   
1. **IntelliTrace 設定**ダイアログ ボックスで、どのイベント ログ、呼び出し情報を収集するかどうか、どのモジュールと収集するプロセスは、ログおよび記録に割り当てる領域の量を指定できます。 IntelliTrace の詳細については、次を参照してください。 [IntelliTrace によるデバッグ](http://go.microsoft.com/fwlink/?LinkId=214468)します。
   
    ![IntelliTrace の設定](./media/vs-azure-tools-intellitrace-debug-published-cloud-services/IC519063.png)

IntelliTrace ログは、IntelliTrace の設定 (既定のサイズは 250 MB) で指定された最大サイズの循環ログ ファイルです。 IntelliTrace ログは、仮想マシンのファイル システム内のファイルに収集されます。 ログを要求するときにスナップショットがその時点で取得され、ローカル コンピューターにダウンロードします。

Azure クラウド サービスは、Azure に発行されていますが後で Azure ノードから IntelliTrace が有効になってかどうかを決定できます**サーバー エクスプ ローラー**、次の図のようにします。

![サーバー エクスプ ローラー - IntelliTrace を有効になっています。](./media/vs-azure-tools-intellitrace-debug-published-cloud-services/IC744134.png)

## <a name="download-intellitrace-logs-for-a-role-instance"></a>ロール インスタンスの IntelliTrace ログをダウンロードします。
Visual Studio を使用して、次の手順に従って、ロール インスタンスの IntelliTrace ログをダウンロードできます。

1. **サーバー エクスプ ローラー**、展開、 **Cloud Services**ノード、ロール インスタンスのログをダウンロードするを見つけます。 

1. ロール インスタンスを右クリックし、コンテキスト メニューから選択**IntelliTrace ログを表示する**します。 

    ![IntelliTrace ログの表示 メニュー オプション](./media/vs-azure-tools-intellitrace-debug-published-cloud-services/view-intellitrace-logs.png)

1. IntelliTrace ログは、ローカル コンピューター上のディレクトリにファイルにダウンロードされます。 ログオンするたびに、IntelliTrace を要求する、新しいスナップショットが作成されます。 Visual Studio での操作の進行状況を表示、ログのダウンロード中は、 **Azure アクティビティ ログ**ウィンドウ。 次の図に示すように、詳細を表示する操作の行アイテムを展開できます。

![VST_IntelliTraceDownloadProgress](./media/vs-azure-tools-intellitrace-debug-published-cloud-services/IC745551.png)

IntelliTrace ログのダウンロード中も、Visual Studio で作業を続行することができます。 ログのダウンロードが完了したら、Visual Studio で開きます。

> [!NOTE]
> IntelliTrace ログには、フレームワークが生成し、後で処理する例外が含まれます。 内部フレームワーク コードには、安全に無視する場合がありますので、ロールの起動時の通常の一部としてこれらの例外が生成されます。
> 
> 

## <a name="next-steps"></a>次の手順
- [Azure クラウド サービスをデバッグするためのオプション](vs-azure-tools-debugging-cloud-services-overview.md)
- [Visual Studio を使用して、Azure クラウド サービスの発行](vs-azure-tools-publishing-a-cloud-service.md)