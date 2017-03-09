---
title: "The connection string contains credentials with a clear text password and is not using integrated security | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 501d85af-92e0-4471-b280-8a59c0688575
caps.latest.revision: 3
caps.handback.revision: 1
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# The connection string contains credentials with a clear text password and is not using integrated security
重要情報を含む接続文字列を現在の DBML ファイルとアプリケーション構成ファイルに保存しますか? 重要情報を含めずに接続文字列を保存する場合は、\[いいえ\] をクリックします。  
  
 機密情報 \(接続文字列に含まれているパスワード\) を含むデータ接続を扱う場合は、接続文字列をプロジェクトの DBML ファイルおよびアプリケーション構成ファイルに保存するときに、機密情報を含めるかどうかを選択するオプションが提供されます。  
  
> [!WARNING]
>  **\[接続\]** プロパティの **\[アプリケーション設定\]** プロパティが明示的に **\[False\]** に設定されている場合、パスワードは DBML ファイルに追加されます。  
  
### 接続文字列を機密情報と共にプロジェクトのアプリケーション設定に保存するには  
  
-   **\[はい\]** をクリックします。  
  
     接続文字列がアプリケーション設定として格納されます。接続文字列には、プレーンテキストの機密情報が含まれます。DBML ファイルには機密情報は含まれません。  
  
### 機密情報を含めずに接続文字列をプロジェクトのアプリケーション設定に保存するには  
  
-   **\[いいえ\]** をクリックします。  
  
     接続文字列がアプリケーション設定として格納されますが、パスワードは含まれません。  
  
## 参照  
 [Object Relational Designer \(O\/R Designer\)](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [Visual Studio でのデータへの接続](../data-tools/connecting-to-data-in-visual-studio.md)