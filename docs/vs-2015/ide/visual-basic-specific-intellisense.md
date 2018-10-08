---
title: Visual Basic 固有の IntelliSense | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IntelliSense [Visual Basic]
- IntelliSense [Visual Studio], Visual Basic
ms.assetid: 4dec8753-05e5-4f74-b304-5f8c4ed8723b
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9bae55b10695ba73fec86d7ab63943e3440e3f05
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47547582"
---
# <a name="visual-basic-specific-intellisense"></a>Visual Basic 固有の IntelliSense
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[Visual Basic-specific IntelliSense](https://docs.microsoft.com/visualstudio/ide/visual-basic-specific-intellisense)します。  
  
Visual Basic ソース コード エディターでは、次の IntelliSense 機能が提供されます。  
  
-   構文のヒント  
  
     構文のヒントには、入力中のステートメントの構文が表示されます。 これは、[Declare](http://msdn.microsoft.com/library/d3f21fb0-b804-4c99-97ed-583b23894cf1) などのステートメントで役立ちます。  
  
## <a name="automatic-completion"></a>自動補完  
  
-   さまざまなキーワードの補完  
  
     たとえば、`goto` とスペースを入力した場合、IntelliSense ではドロップダウン メニューに定義されたラベルのリストが表示されます。 その他のサポートされているキーワードには、`Exit`、`Implements`、`Option`、および `Declare` が含まれます。  
  
-   `Enum` および `Boolean` での補完  
  
     ステートメントが列挙型のメンバーを参照する場合、IntelliSense では `Enum` のメンバーのリストが表示されます。 ステートメントが `Boolean` を参照する場合、IntelliSense では true-false ドロップダウン メニューが表示されます。  
  
 既定で補完機能を無効にするには、**[Visual Basic]** フォルダーの **[全般]** プロパティ ページで、**[自動メンバー表示]** の選択を解除します。  
  
 メンバーの一覧、入力候補、または Alt + 右方向キーを起動することにより、補完機能を手動で起動することができます。 詳細については、「[IntelliSense の使用](../ide/using-intellisense.md)」を参照してください。  
  
## <a name="intellisense-in-zone"></a>ゾーン内の IntelliSense  
 ゾーン内の IntelliSense は、[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] を使用してアプリケーションを配置する必要があり、部分信頼設定に制限された Visual Basic 開発者を支援します。 この機能を使用すると、次のことが可能になります。  
  
-   アプリケーションを実行するアクセス許可を選択する。  
  
-   [メンバーの一覧] で選択したゾーンの API を使用可能なものとして表示し、追加のアクセス許可が必要な API を使用できないものとして表示する。  
  
 詳細については、「[ClickOnce アプリケーションのコード アクセス セキュリティ](../deployment/code-access-security-for-clickonce-applications.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [IntelliSense の使用](../ide/using-intellisense.md)



