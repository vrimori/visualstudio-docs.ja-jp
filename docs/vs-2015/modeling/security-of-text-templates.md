---
title: テキスト テンプレートのセキュリティ |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- text templates, security
ms.assetid: 567a2383-7d43-4acc-af4a-cd70b7a0151e
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 65b4b6616921dae0abb0bb54316d8b8262d1f652
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49214683"
---
# <a name="security-of-text-templates"></a>テキスト テンプレートのセキュリティ
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

テキスト テンプレートには、次のセキュリティの懸念事項があります。  
  
-   テキスト テンプレートは、任意のコードが挿入される脆弱です。  
  
-   ホストがディレクティブ プロセッサの検索に使用するメカニズムが安全でない場合は、悪意のあるディレクティブ プロセッサを実行できます。  
  
## <a name="arbitrary-code"></a>任意のコード  
 テンプレートを記述するときに、内のコードを配置することができます、 \<## > タグです。 これにより、任意のコードをテキスト テンプレート内から実行できます。  
  
 必ず、信頼できるソースからテンプレートを取得します。 信頼できる発行元から提供されないテンプレートを実行しないようにアプリケーションのエンドユーザーに警告するを確認します。  
  
## <a name="malicious-directive-processor"></a>悪意のあるディレクティブ プロセッサ  
 テキスト テンプレート エンジンは、テンプレート テキストを出力ファイルに変換するには、変換のホストと 1 つまたは複数のディレクティブ プロセッサと対話します。 詳細については、次を参照してください。 [、テキスト テンプレート変換プロセス](../modeling/the-text-template-transformation-process.md)します。  
  
 ホストがディレクティブ プロセッサの検索に使用するメカニズムが安全でない場合は、悪意のあるディレクティブ プロセッサを実行するリスクが実行されます。 悪意のあるディレクティブ プロセッサで実行されるコードを提供できます`FullTrust`モード テンプレートを実行するとします。 カスタム テキスト テンプレート変換ホストを作成する場合は、ディレクティブ プロセッサを検索エンジンに対して、レジストリなど、セキュリティで保護されたメカニズムを使用する必要があります。



