---
title: テキスト テンプレートのセキュリティ
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, security
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 71052a0d4120a74269f2aa05412230284271e574
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
ms.locfileid: "31947522"
---
# <a name="security-of-text-templates"></a>テキスト テンプレートのセキュリティ
テキスト テンプレートでは、次のセキュリティに関する注意事項があります。

-   テキスト テンプレートは、任意のコードが挿入される点で脆弱です。

-   ホストがディレクティブ プロセッサの検索に使用するメカニズムが安全でない場合は、悪意のあるディレクティブ プロセッサを実行する可能性があります。

## <a name="arbitrary-code"></a>任意のコード
 テンプレートを記述するときは、 \<## > タグ内にコードを配置します。 これにより、任意のコードをテキスト テンプレート内から実行できます。

 信頼できるソースからテンプレートを取得していることを確認します。 信頼できる発行元から付属していないテンプレートを実行しないようにアプリケーションのエンドユーザーに警告していることを確認してください。

## <a name="malicious-directive-processor"></a>悪意のあるディレクティブ プロセッサ
 テキスト テンプレート エンジンは、出力ファイルへテンプレート テキストを変換するときに、変換ホストと 1 つまたは複数のディレクティブ プロセッサと対話します。 詳細については、次を参照してください。 [テキスト テンプレート変換プロセス](../modeling/the-text-template-transformation-process.md)です。

 ホストがディレクティブ プロセッサの検索に使用するメカニズムが安全でない場合は、悪意のあるディレクティブ プロセッサを実行するリスクがあります。 悪意のあるディレクティブ プロセッサは、テンプレートを実行するときに`FullTrust`モードで実行されるコードを提供する可能性があります。 カスタム テキスト テンプレート変換ホストを作成する場合は、ディレクティブ プロセッサを検索するエンジンのためにレジストリなど、セキュリティで保護されたメカニズムを使用しなければなりません。
