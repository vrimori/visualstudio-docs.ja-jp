---
title: "方法: ClickOnce アプリケーションのカスタム アクセス許可を設定 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce applications, permissions
- permissions, ClickOnce applications
ms.assetid: 660459ca-ef73-44a8-b323-610001f63b93
caps.latest.revision: "17"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 0e99583b9222e71421e548b0cdf1338e81c3c45b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-set-custom-permissions-for-a-clickonce-application"></a>方法 : ClickOnce アプリケーションのカスタム アクセス許可を設定する
インターネット ゾーンまたはローカル イントラネット ゾーンの既定のアクセス許可を使用する [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーションを配置できます。 または、アプリケーションに必要な特定のアクセス許可用にカスタム ゾーンを作成することもできます。 そのためには、 **プロジェクト デザイナー** の **[セキュリティ]**ページでセキュリティのアクセス許可をカスタマイズします。  
  
### <a name="to-customize-a-permission"></a>アクセス許可をカスタマイズするには  
  
1.  **ソリューション エクスプ ローラー**でプロジェクトを選択し、 **[プロジェクト]** メニューの **[プロパティ]**をクリックします。  
  
2.  **[セキュリティ]** タブをクリックします。  
  
3.  **[ClickOnce セキュリティ設定を有効にする]** チェック ボックスをオンにします。  
  
4.  **[これは部分的に信頼するアプリケーションです]** オプション ボタンを選択します。  
  
     **[ClickOnce セキュリティのアクセス許可]** セクション内のコントロールが有効になります。  
  
5.  **[アプリケーションのインストール元のゾーン]** ドロップダウン リストの **[(カスタム)]**を選択します。  
  
6.  **[アクセス許可 XML の編集]**をクリックします。  
  
     XML エディターで app.manifest ファイルが開きます。  
  
7.  `</applicationRequestMinimum>` 要素の前に、アプリケーションに必要なアクセス許可の XML コードを追加します。  
  
    > [!NOTE]
    >  アクセス許可セットの `ToXml` メソッドを使用して、アプリケーション マニフェスト用の XML コードを生成できます。 たとえば、 <xref:System.Security.Permissions.EnvironmentPermission> アクセス許可セットの XML を生成するには、 <xref:System.Security.Permissions.EnvironmentPermission.ToXml%2A> メソッドを呼び出します。 アクセス許可セット XML の構造の詳細については、「 [NIB: 方法: XML ファイルを使用してアクセス許可セットをインポートする](http://msdn.microsoft.com/en-us/dea16b54-c108-408a-ac36-cdc05f746236)」をご覧ください。  
  
## <a name="see-also"></a>関連項目  
 [ClickOnce アプリケーションのセキュリティ](../deployment/securing-clickonce-applications.md)   
 [ClickOnce アプリケーション用のコード アクセス セキュリティ](../deployment/code-access-security-for-clickonce-applications.md)   
 [ClickOnce アプリケーションのセキュリティ](../deployment/securing-clickonce-applications.md)