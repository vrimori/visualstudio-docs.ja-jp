---
title: 接続文字列にはクリア テキスト パスワード付きの資格情報が含まれていて、統合セキュリティは使用されていません
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 501d85af-92e0-4471-b280-8a59c0688575
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: bf8a8fc3bb024c1eb8ee7baf91856a54dcb9d21f
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
ms.locfileid: "31922613"
---
# <a name="the-connection-string-contains-credentials-with-a-clear-text-password-and-is-not-using-integrated-security"></a>接続文字列にはクリア テキスト パスワード付きの資格情報が含まれていて、統合セキュリティは使用されていません

重要情報を含む接続文字列を現在の DBML ファイルとアプリケーション構成ファイルに保存しますか?   重要情報を含めずに接続文字列を保存する場合は、[いいえ] をクリックします。

機密情報 (接続文字列に含まれているパスワード) を含むデータ接続を扱う場合は、接続文字列をプロジェクトの DBML ファイルおよびアプリケーション構成ファイルに保存するときに、機密情報を含めるかどうかを選択するオプションが提供されます。

> [!WARNING]
> 明示的に設定する、**接続**プロパティ**アプリケーション設定**プロパティを**False**パスワードは DBML ファイルに追加されます。

## <a name="to-save-the-connection-string-with-the-sensitive-information-in-the-projects-application-settings"></a>接続文字列を機密情報と共にプロジェクトのアプリケーション設定に保存するには

- **[はい]** をクリックします。

   接続文字列がアプリケーション設定として格納されます。 接続文字列には、プレーンテキストの機密情報が含まれます。 DBML ファイルには機密情報は含まれません。

## <a name="to-save-the-connection-string-without-the-sensitive-information-in-the-projects-application-settings"></a>機密情報を含めずに接続文字列をプロジェクトのアプリケーション設定に保存するには

- **[いいえ]** をクリックします。

   接続文字列がアプリケーション設定として格納されますが、パスワードは含まれません。

## <a name="see-also"></a>関連項目

- [O/R デザイナーのメッセージ](../data-tools/o-r-designer-messages.md)
- [Visual Studio での LINQ to SQL ツールします。](../data-tools/linq-to-sql-tools-in-visual-studio2.md)