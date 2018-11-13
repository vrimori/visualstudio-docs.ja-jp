---
title: Emulator Express を使用した実行し、ローカル コンピューターでの Azure クラウド サービスをデバッグする |Microsoft Docs
description: Emulator Express を使用した実行し、ローカル コンピューター上のクラウド サービスをデバッグするには
author: mikejo5000
manager: douge
ms.assetid: 73108f98-a552-4817-b7a1-551367b71906
ms.topic: conceptual
ms.workload: azure-vs
ms.date: 03/06/2017
ms.author: mikejo
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.openlocfilehash: 28dd59e3d691df0199afffe93d68d60668c6afe4
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002342"
---
# <a name="using-emulator-express-to-run-and-debug-an-azure-cloud-service-on-a-local-machine"></a>Emulator Express を使用したローカル コンピューターでの Azure クラウド サービスの実行とデバッグ
Emulator Express を使用すると、テストでき、管理者として Visual Studio を実行することがなくクラウド サービスをデバッグすることができます。 Emulator Express またはクラウド サービスの要件に応じて、完全なエミュレーターのいずれかを使用するプロジェクトの設定を設定することができます。 フル装備のエミュレーターの詳細については、次を参照してください。[コンピューティング エミュレーターで Azure アプリケーションの実行](/azure/storage/common/storage-use-emulator)します。

## <a name="using-emulator-express-in-visual-studio"></a>Visual Studio での Emulator Express の使用
Azure SDK 2.3 以降での Azure プロジェクトを作成するときに Emulator Express が自動的に使用します。 Azure SDK の以前のバージョンで作成された既存のプロジェクトでは、Emulator Express を選択するのに、次の手順を使用します。

1. 作成または Visual Studio で Azure クラウド サービス プロジェクトを開きます。

1. **ソリューション エクスプ ローラー**プロジェクトを右クリックし、コンテキスト メニューから選択、**プロパティ**します。

1. プロジェクト プロパティのページで、選択、 **Web**タブ。

    ![Azure クラウド サービス プロジェクトのプロパティ](./media/vs-azure-tools-emulator-express-debug-run/web-properties.png)

1. **ローカル開発サーバー**、**オプションの IIS Express を使用**します。

1. **エミュレーター**、 **Emulator Express を使用**します。
   
1. Emulator Express を起動するには、コマンド プロンプトで次のコマンドを実行します。 

    ```
    csrun.exe /useemulatorexpress
    ```

## <a name="emulator-express-limitations"></a>Emulator Express の制限事項
次の問題には、Emulator Express の制限事項が確認されています。 

- Emulator Express は、IIS Web サーバーと互換性がありません。
- クラウド サービスが複数のロールを含めることができますが、各ロールは 1 つのインスタンスに制限されます。
- 1,000 未満のポート番号にアクセスすることはできません。 通常 1,000 未満のポートを使用する認証プロバイダーを使用する場合は、この値を 1,000 を超えるポート番号に変更する必要があります。
- Azure コンピューティング エミュレーターに適用される制限事項は、Emulator Express にも適用されます。 たとえば、デプロイあたり 50 個以上のロール インスタンスを持つことはできません。 Azure コンピューティング エミュレーターの詳細については、次を参照してください。[コンピューティング エミュレーターで Azure アプリケーションの実行](http://go.microsoft.com/fwlink/p/?LinkId=623050)します。

## <a name="next-steps"></a>次の手順
[Azure cloud services のデバッグ](https://msdn.microsoft.com/library/azure/ee405479.aspx)
