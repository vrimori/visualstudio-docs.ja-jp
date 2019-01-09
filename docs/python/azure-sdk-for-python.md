---
title: Azure SDK for Python
description: Azure SDK for Python を使うと、任意のプラットフォームで実行している Python アプリケーションから Microsoft Azure サービスを簡単に利用できるようになります。
ms.date: 12/06/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
- azure
ms.openlocfilehash: db391b30305e3fad8384dcbeea611379f0061054
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53854218"
---
# <a name="consume-azure-services-using-the-azure-sdk-for-python"></a>Azure SDK for Python を使用して Azure サービスを使用する

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

- [Linux 上の Azure App Service に Web アプリを作成する](/azure/app-service/containers/quickstart-python)。
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
