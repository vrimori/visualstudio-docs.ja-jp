---
title: 接続文字列がクリア テキスト パスワードを使用して資格情報を含むし、統合セキュリティを使用していない |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 501d85af-92e0-4471-b280-8a59c0688575
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f1ec13cab1b8c41225cb1934740b8dd3e7f59ac0
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49230876"
---
# <a name="the-connection-string-contains-credentials-with-a-clear-text-password-and-is-not-using-integrated-security"></a>接続文字列にはクリア テキスト パスワード付きの資格情報が含まれていて、統合セキュリティは使用されていません
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
重要情報を含む接続文字列を現在の DBML ファイルとアプリケーション構成ファイルに保存しますか?   重要情報を含めずに接続文字列を保存する場合は、[いいえ] をクリックします。  
  
 機密情報 (接続文字列に含まれているパスワード) を含むデータ接続を扱う場合は、接続文字列をプロジェクトの DBML ファイルおよびアプリケーション構成ファイルに保存するときに、機密情報を含めるかどうかを選択するオプションが提供されます。  
  
> [!WARNING]
>  明示的に設定、**接続**プロパティ**アプリケーション設定**プロパティを**False**は DBML ファイルにパスワードを追加します。  
  
### <a name="to-save-the-connection-string-with-the-sensitive-information-in-the-projects-application-settings"></a>接続文字列を機密情報と共にプロジェクトのアプリケーション設定に保存するには  
  
-   **[はい]** をクリックします。  
  
     接続文字列がアプリケーション設定として格納されます。 接続文字列には、プレーンテキストの機密情報が含まれます。 DBML ファイルには機密情報は含まれません。  
  
### <a name="to-save-the-connection-string-without-the-sensitive-information-in-the-projects-application-settings"></a>機密情報を含めずに接続文字列をプロジェクトのアプリケーション設定に保存するには  
  
-   **[いいえ]** をクリックします。  
  
     接続文字列がアプリケーション設定として格納されますが、パスワードは含まれません。  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio の LINQ to SQL ツール](../data-tools/linq-to-sql-tools-in-visual-studio2.md)

