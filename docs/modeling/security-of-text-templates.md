---
title: "テキスト テンプレートのセキュリティ |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: text templates, security
ms.assetid: 567a2383-7d43-4acc-af4a-cd70b7a0151e
caps.latest.revision: "23"
author: alancameronwills
ms.author: awills
manager: douge
ms.workload: multiple
ms.openlocfilehash: fc8827357ed3612dd47aca296719ace281839b0e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="security-of-text-templates"></a>テキスト テンプレートのセキュリティ
テキスト テンプレートでは、次のセキュリティに関する注意事項があります。  
  
-   テキスト テンプレートは、任意のコードが挿入される脆弱です。  
  
-   ホストがディレクティブ プロセッサの検索に使用するメカニズムが安全でない場合は、悪意のあるディレクティブ プロセッサを実行する可能性があります。  
  
## <a name="arbitrary-code"></a>任意のコード  
 内のコードを配置できるテンプレートを記述するときに、 \<## > タグです。 これにより、任意のコードをテキスト テンプレート内から実行できます。  
  
 信頼できるソースからテンプレートを取得することを確認します。 信頼できる発行元から付属していないテンプレートを実行しないようにアプリケーションのエンドユーザーに警告することを確認してください。  
  
## <a name="malicious-directive-processor"></a>悪意のあるディレクティブ プロセッサ  
 テキスト テンプレート エンジンは、出力ファイルへテンプレート テキストを変換するには、変換ホストと 1 つまたは複数のディレクティブ プロセッサと対話します。 詳細については、次を参照してください。 [、テキスト テンプレート変換プロセス](../modeling/the-text-template-transformation-process.md)です。  
  
 ホストがディレクティブ プロセッサの検索に使用するメカニズムが安全でない場合は、悪意のあるディレクティブ プロセッサを実行するリスクが実行されます。 悪意のあるディレクティブ プロセッサで実行されるコードを提供できます`FullTrust`モード テンプレートを実行するとします。 カスタム テキスト テンプレート変換ホストを作成する場合は、ディレクティブ プロセッサを検索するエンジンに、レジストリなど、セキュリティで保護されたメカニズムを使用する必要があります。