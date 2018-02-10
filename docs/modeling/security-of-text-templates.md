---
title: "テキスト テンプレートのセキュリティ |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
helpviewer_keywords:
- text templates, security
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 5c6b8d64e02562887b2bc438943fdfe7be3b2e1c
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
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