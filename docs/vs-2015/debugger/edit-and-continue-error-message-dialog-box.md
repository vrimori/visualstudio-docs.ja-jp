---
title: エディット コンティニュのエラー メッセージ ダイアログ ボックス |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.ENC.SupportedButNotAvaiable
- vs.debug.ENC.CannotEditWhileException
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Edit and Continue Error Message dialog box
ms.assetid: f98c91c0-447a-4533-85b6-87170a0dc4c3
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c311f6243ddbf087fd18fd9209e2e17bbe3065a6
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51771324"
---
# <a name="edit-and-continue-error-message-dialog-box"></a>エディット コンティニュ エラー メッセージ ダイアログ ボックス
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

エディット コンティニュをサポートする言語でデバッグするときに、このダイアログ ボックスが表示されますが、**エディット コンティニュ**は行ったコード変更の種類を使用できません。 ダイアログ ボックス内のエラー メッセージに、より詳しい説明が示されます。 このダイアログ ボックスが表示される原因としては、次のことが考えられます。  
  
-   アンマネージド デバッグを有効にしているときに、マネージド コードを編集しようとした。 混合モード デバッグを実行している場合は、エディット コンティニュを使用できません。  
  
-   SQL Server コードを編集しようとした。  
  
-   ワトソン博士のダンプをデバッグしているときに、デバッグ  
  
-   ハンドルされない例外が発生した後のコードと、オプションを編集しようとしています。"**ハンドルされない例外でコール スタックをアンワインド**"が選択されていません。  
  
-   埋め込まれたランタイム アプリケーションをデバッグしているときに、コードを編集しようとした。  
  
-   開始する代わりに、アタッチするプログラム コードを編集しようとした、**デバッグ**メニュー。  
  
-   最適化されたコードを編集しようとした。  
  
-   デバッグ対象が 64 ビット アプリケーションである場合に、マネージド コードをデバッグしようとした。 エディット コンティニュを使用する場合は、デバッグ対象を x86 に設定する必要があります  (*プロジェクト***プロパティ**、**コンパイル** タブで、**高度なコンパイラ**設定します。)。  
  
-   デバッグ中に変更され、再読み込みされたアセンブリのコードを編集しようとした。  
  
-   読み込まれていないアセンブリのコードを編集しようとした。  
  
-   新しいバージョンでビルド エラーが発生したため、古いバージョンでアプリケーションのデバッグを開始した。  
  
-   実行中のコードを編集しようとした。  
  
## <a name="uielement-list"></a>UIElement の一覧  
 **わかりました**  
 ダイアログ ボックスを閉じ、直前の編集操作をキャンセルします。  
  
## <a name="see-also"></a>関連項目  
 [サポートされているコード変更 (C++)](../debugger/supported-code-changes-cpp.md)



