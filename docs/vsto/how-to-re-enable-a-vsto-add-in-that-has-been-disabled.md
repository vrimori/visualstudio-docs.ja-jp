---
title: "方法: 無効になっている VSTO アドインを有効に再 |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VST.Warning.DisabledAddIn
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- disabled add-ins
- add-ins [Office development in Visual Studio], disabled
- add-ins [Office development in Visual Studio], enabling
ms.assetid: 69719a0a-984c-42cd-80a2-1367c866e5df
caps.latest.revision: "27"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 0b54ad4592e22f828074ef29d734f7f9441921f9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-re-enable-a-vsto-add-in-that-has-been-disabled"></a>方法: 無効にされた VSTO アドインを再度有効にする
  Microsoft Office アプリケーションにより、予期しない動作をする VSTO アドインが無効にされる場合があります。 VSTO アドインをデバッグする際に、アプリケーションが VSTO アドインを読み込まない場合は、アプリケーションにより VSTO アドインがハードに無効化、またはソフトに無効化されている可能性があります。  
  
 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]  
  
## <a name="hard-disabled-vsto-add-ins"></a>ハードに無効化された VSTO アドイン  
 ハード的な無効化は、VSTO アドインによってアプリケーションが予期せずに終了した場合に発生する可能性があります。 また、開発用コンピューターで VSTO アドインの <xref:Microsoft.Office.Tools.AddIn.Startup> イベント ハンドラーの実行中にデバッガーを停止した場合にも発生することがあります。  
  
#### <a name="to-re-enable-a-vsto-add-in"></a>VSTO アドインを再度有効にするには  
  
1.  アプリケーションで **[ファイル]** タブをクリックします。  
  
2.  *[ApplicationName* **オプション]** ボタンをクリックします。  
  
3.  [カテゴリ] ウィンドウで **[アドイン]**をクリックします。  
  
4.  詳細ウィンドウで、「 **無効になっているアプリケーション アドイン** 」リストに VSTO アドインが表示されていることを確認します。  
  
     **[名前]** 列でアセンブリの名前を指定し、 **[場所]** 列でアプリケーション マニフェストの完全なパスを指定します。  
  
5.  **[管理]** ボックスで、 **[無効になっている項目]**をクリックしてから **[移動]**をクリックします。  
  
6.  VSTO アドインを選択し、 **[有効にする]**をクリックします。  
  
7.  **[閉じる]** をクリックします。  
  
## <a name="soft-disabled-vsto-add-ins"></a>ソフトに無効化された VSTO アドイン  
 ソフトな無効化は、VSTO アドインによってエラーが発生したが、アプリケーションが予期せずに終了するということがなかったという場合に発生する可能性があります。 たとえば、 <xref:Microsoft.Office.Tools.AddIn.Startup> イベント ハンドラーの実行中に VSTO アドインによってハンドルされない例外がスローされた場合に、アプリケーションによってそのアドインがソフトに無効化されることがあります。  
  
> [!NOTE]  
>  ソフトに無効化された VSTO アドインを再度有効にすると、アプリケーションはただちに VSTO アドインの読み込みを試みます。 アプリケーションにより VSTO アドインがソフトに無効化された当初の原因であった問題が解決されていない場合は、アプリケーションにより VSTO アドインが再度ソフトに無効化されます。  
  
#### <a name="to-re-enable-an-vsto-add-in"></a>VSTO アドインを再度有効にするには  
  
1.  アプリケーションで **[ファイル]** タブをクリックします。  
  
2.  *[ApplicationName* **オプション]** ボタンをクリックします。  
  
3.  [カテゴリ] ウィンドウで **[アドイン]**をクリックします。  
  
4.  詳細ウィンドウで、「 **非アクティブなアプリケーション アドイン** 」リストに VSTO アドインが表示されていることを確認します。  
  
     **[名前]** 列でアセンブリの名前を指定し、 **[場所]** 列でアプリケーション マニフェストの完全なパスを指定します。  
  
5.  **[管理]** ボックスで、 **[COM アドイン]**をクリックしてから **[移動]**をクリックします。  
  
6.  **[COM アドイン]** ダイアログ ボックスで、無効になっている VSTO アドインの横のチェック ボックスをオンにします。  
  
7.  **[OK]**をクリックします。  
  
## <a name="see-also"></a>参照  
 [Office ソリューションのビルド](../vsto/building-office-solutions.md)   
 [Office プロジェクトのデバッグ](../vsto/debugging-office-projects.md)   
 [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md)  
  
  