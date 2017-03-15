---
title: "Visual Basic 固有の IntelliSense | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IntelliSense [Visual Basic]"
  - "IntelliSense [Visual Studio], Visual Basic"
ms.assetid: 4dec8753-05e5-4f74-b304-5f8c4ed8723b
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 10
---
# Visual Basic 固有の IntelliSense
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Visual Basic のソース コード エディターには、以下の IntelliSense の機能が用意されています。  
  
-   構文ヒント  
  
     構文ヒントでは、入力中のステートメントの構文が表示されます。  この機能は、[Declare](/dotnet/visual-basic/language-reference/statements/declare-statement) などのステートメントで役立ちます。  
  
## 自動補完  
  
-   さまざまなキーワードの補完入力  
  
     たとえば、「`goto`」と入力して **Space** キーを押すと、IntelliSense は定義されたラベルの一覧をドロップダウン メニューに表示します。  その他のキーワードとして、`Exit`、`Implements`、`Option`、および `Declare` がサポートされています。  
  
-   `Enum` と `Boolean` での補完  
  
     ステートメントが列挙型のメンバーを参照する場合は、IntelliSense では `Enum` のメンバーを一覧表示します。  ステートメントがブール型のメンバーを参照する場合は、IntelliSense では True または False のドロップダウン メニューを表示します。  
  
 既定で補完機能を無効にするには、**\[Visual Basic\]** フォルダーの **\[全般\]** プロパティ ページで、**\[自動メンバー表示\]** の選択を解除します。  
  
 メンバーの一覧、入力候補、または alt キーを押しながら右方向キーを起動することにより、完了を手動で起動することができます。  詳細については、「[IntelliSense の使用方法](../ide/using-intellisense.md)」を参照してください。  
  
## ゾーン内の IntelliSense  
 ゾーン内の IntelliSenseは、部分信頼設定に制限された Visual Basic 開発者が、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] を使用してアプリケーションを配置する作業を支援する機能です。  この機能を使用すると、次のことが可能になります。  
  
-   アプリケーションを実行するアクセス許可を選択できます。  
  
-   \[メンバーの一覧\] で、選択したゾーンの API を利用可能な API として表示し、追加のアクセス許可が必要な API を利用できない API として表示できます。  
  
 詳細については、「[ClickOnce アプリケーションのコード アクセス セキュリティ](../deployment/code-access-security-for-clickonce-applications.md)」を参照してください。  
  
## 参照  
 [IntelliSense の使用方法](../ide/using-intellisense.md)