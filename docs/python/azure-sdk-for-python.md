---
title: Azure SDK for Python
description: Azure SDK for Python を使うと、任意のプラットフォームで実行している Python アプリケーションから Microsoft Azure サービスを簡単に利用できるようになります。
ms.date: 10/10/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
- azure
ms.openlocfilehash: b1b41fe707c751b5cd32706d1c27f707f964dff8
ms.sourcegitcommit: 40b6438b5acd7e59337a382c39ec711b9e99cc8a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/11/2018
ms.locfileid: "49100927"
---
# <a name="azure-sdk-for-python"></a>Azure SDK for Python

Azure SDK for Python を使用すると、Windows、MacOS、Linux で実行されているアプリケーションからの Microsoft Azure サービスの使用と管理が簡単になります。

## <a name="installation"></a>インストール

Azure SDK は [Python のパッケージ インデックス](https://pypi.python.org/pypi/azure)からインストールします。

次のように、**最新の安定したバージョン** (Python 2.7 および 3.x をサポート) をインストールします。

```command
pip install azure
```

Azure ドキュメントの「[Python と SDK のインストール](https://docs.microsoft.com/azure/python-how-to-install/)」の手順に従ってインストールすることもできます。

## <a name="documentation"></a>ドキュメント

「[Python デベロッパー センター](https://docs.microsoft.com/python/azure/?view=azure-python)」にも、さまざまなチュートリアルを含む有用なリソースが数多く用意されています。

- Linux 上の Azure App Service に Web アプリを作成する (/azure/app-service/containers/quickstart-python)。
- [Python から Azure BLOB ストレージを使用する方法](/azure/storage/blobs/storage-quickstart-blobs-python)
- [Python から Table ストレージを使用する方法](/azure/cosmos-db/table-storage-how-to-use-python)
- [Python から Queue ストレージを使用する方法](/azure/storage/storage-python-how-to-use-queue-storage)
- [Azure Cosmos DB](/azure/cosmos-db/sql-api-python-application)
- [Service Bus キューの使用方法](/azure/service-bus-messaging/service-bus-python-how-to-use-queues)
- [Service Bus のトピックとサブスクリプションの使用方法](/azure/service-bus-messaging/service-bus-python-how-to-use-topics-subscriptions)
- [Python からサービス管理を使用する方法](/azure/cloud-services/cloud-services-python-how-to-use-service-management)

ドキュメントのないパブリック API に関しては、[SDK の GitHub リポジトリ](https://github.com/Azure/azure-sdk-for-python)の単体テストが有益な情報源になります。

- [ストレージの単体テスト](https://github.com/Azure/azure-storage-python/tree/master/tests)に関するページ
- [Service Bus の単体テスト](https://github.com/Azure/azure-sdk-for-python/tree/master/azure-servicebus/tests)に関するページ
- [サービス管理の単体テスト](https://github.com/Azure/azure-sdk-for-python/tree/master/azure-servicemanagement-legacy/tests)

## <a name="support"></a>サポート

SDK の GitHub リポジトリは、[https://github.com/Azure/azure-sdk-for-python](https://github.com/Azure/azure-sdk-for-python) にあります。

SDK の使用方法についての問題や質問がある場合は、[リポジトリに問題を登録してください](https://github.com/Azure/azure-sdk-for-python/issues)。
