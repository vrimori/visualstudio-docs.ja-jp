---
title: テキスト テンプレートのセキュリティ
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, security
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: 94b2520ffafe3e99420bf77577b59341b6d216aa
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54957209"
---
# <a name="security-of-text-templates"></a>テキスト テンプレートのセキュリティ
テキスト テンプレートには、次のセキュリティの懸念事項があります。

-   テキスト テンプレートは、任意のコードが挿入される点で脆弱です。

-   ホストがディレクティブ プロセッサの検索に使用するメカニズムが安全でない場合は、悪意のあるディレクティブ プロセッサを実行できます。

## <a name="arbitrary-code"></a>任意のコード
 テンプレートを記述するときは、 \<## > タグ内にコードを配置します。 これにより、任意のコードをテキスト テンプレート内から実行できます。

 信頼できるソースからテンプレートを取得していることを確認します。 信頼できる発行元から付属していないテンプレートを実行しないようにアプリケーションのエンドユーザーに警告していることを確認してください。

## <a name="malicious-directive-processor"></a>悪意のあるディレクティブ プロセッサ
 テキスト テンプレート エンジンは、出力ファイルへテンプレート テキストを変換するときに、変換ホストと 1 つまたは複数のディレクティブ プロセッサと対話します。 詳細については、次を参照してください。 [テキスト テンプレート変換プロセス](../modeling/the-text-template-transformation-process.md)です。

 ホストがディレクティブ プロセッサの検索に使用するメカニズムが安全でない場合は、悪意のあるディレクティブ プロセッサを実行するリスクがあります。 悪意のあるディレクティブ プロセッサは、テンプレートを実行するときに`FullTrust`モードで実行されるコードを提供する可能性があります。 カスタム テキスト テンプレート変換ホストを作成する場合は、ディレクティブ プロセッサを検索するエンジンのためにレジストリなど、セキュリティで保護されたメカニズムを使用しなければなりません。
