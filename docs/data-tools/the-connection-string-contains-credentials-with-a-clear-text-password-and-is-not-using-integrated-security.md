---
title: 接続文字列にはクリア テキスト パスワード付きの資格情報が含まれていて、統合セキュリティは使用されていません
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 501d85af-92e0-4471-b280-8a59c0688575
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: 37155efecd7019c0de82d37ee8b071a74a29eea6
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54966531"
---
# <a name="the-connection-string-contains-credentials-with-a-clear-text-password-and-is-not-using-integrated-security"></a>接続文字列にはクリア テキスト パスワード付きの資格情報が含まれていて、統合セキュリティは使用されていません

重要情報を含む接続文字列を現在の DBML ファイルとアプリケーション構成ファイルに保存しますか?   重要情報を含めずに接続文字列を保存する場合は、**[いいえ]** をクリックします。

機密情報 (接続文字列に含まれているパスワード) を含むデータ接続を扱う場合は、接続文字列をプロジェクトの DBML ファイルおよびアプリケーション構成ファイルに保存するときに、機密情報を含めるかどうかを選択するオプションが提供されます。

> [!WARNING]
> **[接続]** プロパティの **[アプリケーション設定]** プロパティが明示的に **[False]** に設定されている場合、パスワードは DBML ファイルに追加されます。

## <a name="save-options"></a>オプションを保存します。

- 機密情報を接続文字列を保存する**はい**します。

   接続文字列がアプリケーション設定として格納されます。 接続文字列には、プレーンテキストの機密情報が含まれます。 DBML ファイルには機密情報は含まれません。

- 機密情報がない場合、接続文字列を保存する**いいえ**します。

   接続文字列がアプリケーション設定として格納されますが、パスワードは含まれません。

## <a name="see-also"></a>関連項目

- [O/R デザイナーのメッセージ](../data-tools/o-r-designer-messages.md)
- [Visual Studio の LINQ to SQL ツール](../data-tools/linq-to-sql-tools-in-visual-studio2.md)