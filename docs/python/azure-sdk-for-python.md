---
title: Azure SDK for Python
description: Azure SDK for Python を使うと、任意のプラットフォームで実行している Python アプリケーションから Microsoft Azure サービスを簡単に利用できるようになります。
ms.date: 06/26/2018
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
ms.openlocfilehash: 4dd7e5841db4c05de5607f9aefe7b9a3a36fee19
ms.sourcegitcommit: 4f82c178b1ac585dcf13b515cc2a9cb547d5f949
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/30/2018
ms.locfileid: "39341239"
---
# <a name="azure-sdk-for-python"></a>Azure SDK for Python

Azure SDK for Python を使用すると、Windows、Mac OSX、Linux で実行されているアプリケーションからの Microsoft Azure サービスの使用と管理が簡単になります。

## <a name="installation"></a>インストール

Azure SDK は [Python のパッケージ インデックス](https://pypi.python.org/pypi/azure)からインストールします。

次のように、**最新の安定したバージョン** (Python 2.7 および 3.x をサポート) をインストールします。

```command
pip install azure
```

Azure ドキュメントの「[Python と SDK のインストール](https://docs.microsoft.com/azure/python-how-to-install/)」の手順に従ってインストールすることもできます。

## <a name="documentation"></a>ドキュメント

ドキュメントは [azure-sdk-for-python.readthedocs.org](https://docs.microsoft.com/en-us/python/azure/?view=azure-python) にあります。

「[Python デベロッパー センター](http://azure.microsoft.com/develop/python/)」にも、さまざまなチュートリアルを含む有用なリソースが数多く用意されています。

- [Django](/azure/app-service-web/web-sites-python-create-deploy-django-app)、[Flask](/azure/app-service-web/web-sites-python-create-deploy-flask-app)、[Bottle](/azure/app-service-web/web-sites-python-create-deploy-bottle-app) を使用した Web アプリの作成
- [Python から Azure BLOB ストレージを使用する方法](/azure/storage/storage-python-how-to-use-blob-storage)
- [Python から Table ストレージを使用する方法](/azure/storage/storage-python-how-to-use-table-storage)
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

SDK の Git リポジトリは、[https://github.com/Azure/azure-sdk-for-python](https://github.com/Azure/azure-sdk-for-python) にあります。

SDK の使用方法についての問題や質問がある場合は、[リポジトリに問題を登録してください](https://github.com/Azure/azure-sdk-for-python/issues)。
