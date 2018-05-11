---
title: '方法: アドイン ユーザー インターフェイス エラーを表示 |Microsoft ドキュメント'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- add-ins [Office development in Visual Studio], user interface errors
- errors [Office development in Visual Studio], user interface errors
- user interfaces [Office development in Visual Studio], errors
- application-level add-ins [Office development in Visual Studio], user interface errors
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 795578d6a168dff5fee259a90abac83fa7788121
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-show-add-in-user-interface-errors"></a>方法 : アドインのユーザー インターフェイス エラーを表示する
  既定では、VSTO アドインが Microsoft Office ユーザー インターフェイス (UI) の操作を試みて失敗しても、エラー メッセージは表示されません。 しかし、UI に関連するエラー メッセージを表示するように Microsoft Office アプリケーションを構成できます。 これらのメッセージを使用すると、カスタム リボンが表示されない原因や、リボンは表示されるもののコントロールが表示されない理由を判断するのに役立ちます。  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
### <a name="to-show-vsto-add-in-user-interface-errors"></a>VSTO アドインのユーザー インターフェイス エラーを表示するには  
  
1.  アプリケーションを起動します。  
  
2.  **[ファイル]** タブをクリックします。  
  
3.  **[オプション]**をクリックします。  
  
4.  [カテゴリ] ウィンドウで **[詳細]**をクリックします。  
  
5.  詳細ウィンドウで、 **[VSTO アドイン ユーザー インターフェイスのエラーを表示する]**を選び、 **[OK]**をクリックします。  
  
    > [!NOTE]  
    >  Outlook の場合、詳細ウィンドウの **[開発]** セクションに **[VSTO アドイン ユーザー インターフェイスのエラーを表示する]** チェック ボックスがあります。 その他のアプリケーションの場合、このチェック ボックスは、詳細ウィンドウの **[全般]** セクションにあります。  
  
## <a name="see-also"></a>関連項目  
 [Office UI のカスタマイズ](../vsto/office-ui-customization.md)   
 [Outlook フォーム領域の作成](../vsto/creating-outlook-form-regions.md)   
 [リボンの概要](../vsto/ribbon-overview.md)   
 [操作ウィンドウの概要](../vsto/actions-pane-overview.md)  
  
  