---
title: エディット コンティニュ (Visual Basic) |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
- VB
helpviewer_keywords:
- Edit and Continue, 64-bit
- Edit and Continue [Visual Basic]
- debugging [Visual Basic], Edit and Continue
- Visual Basic, Edit and Continue
- 64-bit Edit and Continue
ms.assetid: 7e90f34f-e699-45ab-a4c9-a4b527c498c8
caps.latest.revision: 43
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 61ce8f61092bdcc612ea535debfcface976ebff8
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49265118"
---
# <a name="edit-and-continue-visual-basic"></a>エディット コンティニュ (Visual Basic)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

エディット コンティニュは、中断モードでの実行中にコードを変更できるようにするための、[!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 用デバッグ機能です。 コードの編集を適用した後で、新しい編集でコードの実行を再開して編集結果を確認できます。  
  
 エディット コンティニュ機能は、中断モードで使用できます。 中断モードでは、命令ポインター (ソース ウィンドウ内の黄色の矢印) はメソッドまたはプロパティの本体内の実行可能なステートメント上にあり、次に実行される行を指します。 中断モードでは、ほとんどの種類の変更を実行可能なステートメントに加えることができます。この変更は、基になるプロジェクトに取り込まれます。 ただし、一般に、中断モードでは、パブリック メソッド、パブリック フィールド、クラス宣言などの宣言ステートメントの変更はできません。  
  
 許可されない編集を行った場合は、その変更に紫色の波下線が表示され、タスク一覧にタスクが表示されます。 エディット コンティニュを引き続き使用するには、許可されない編集を元に戻さなければなりません。 エディット コンティニュの外部であれば、許可されない編集が認められる場合もあります。 そのような許可されない編集の結果を保持するには、デバッグを停止してアプリケーションを再起動する必要があります。  
  
 エディット コンティニュは、.NET Framework 4.5.1 を対象にする 64 ビット プロジェクトでサポートされています。  
  
 使用してデバッグを開始するときにエディット コンティニュがサポートされていません**プロセスにアタッチ**します。 エディット コンティニュは、最適化されたコード、マネージド コードとネイティブ コードの混合コード、または Compact Framework (スマート デバイス) プロジェクトではサポートされていません。  
  
 このセクションの各トピックでは、この機能の使用方法と許可されない種類の変更について詳しく説明します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [方法 : エディット コンティニュの中断モード時に編集を適用する](../debugger/how-to-apply-edits-in-break-mode-with-edit-and-continue.md)  
 中断モードにおいてコードの編集を適用する方法について説明します。  
  
 [Visual Basic エディット コンティニュでサポートされていない編集](../debugger/unsupported-edits-in-visual-basic-edit-and-continue.md)  
 [!INCLUDE[vb_current_short](../includes/vb-current-short-md.md)] エディット コンティニュで実行できない編集の種類について説明します。  
  
## <a name="related-sections"></a>関連項目  
 [エディット コンティニュ](../debugger/edit-and-continue.md)  
 エディット コンティニュに関するトピックの一覧を提供します。



