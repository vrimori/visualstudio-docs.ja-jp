---
title: "エディット コンティニュ (Visual Basic) |Microsoft ドキュメント"
ms.custom: 
ms.date: 10/11/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue, 64-bit
- Edit and Continue [Visual Basic]
- debugging [Visual Basic], Edit and Continue
- Visual Basic, Edit and Continue
- 64-bit Edit and Continue
ms.assetid: 7e90f34f-e699-45ab-a4c9-a4b527c498c8
caps.latest.revision: "40"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 82ec43b02895c2067b04f52f893184a82dd0f36b
ms.sourcegitcommit: 5d43e9590e2246084670b79269cc9d99124bb3df
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="edit-and-continue-visual-basic"></a>エディット コンティニュ (Visual Basic)
エディット コンティニュは、中断モードでの実行中にコードを変更できるようにするための、[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 用デバッグ機能です。 コードの編集を適用した後で、新しい編集でコードの実行を再開して編集結果を確認できます。  
  
 エディット コンティニュ機能は、中断モードで使用できます。 中断モード、命令ポインター、黄色の矢印がソース ウィンドウでは、ポイントとなるメソッドまたはプロパティ本体の実行可能なステートメントを含む行には、次へ を実行します。

 エディット コンティニュは、デバッグ セッションで行う必要があるほとんどの変更をサポートしますが、いくつか例外があります。 詳細については、次を参照してください。 [(c# および Visual Basic) のサポートされているコード変更](../debugger/supported-code-changes-csharp.md)です。   
  
 許可されない編集を行った場合は、その変更に紫色の波下線が表示され、タスク一覧にタスクが表示されます。 エディット コンティニュを引き続き使用するには、許可されない編集を元に戻さなければなりません。 エディット コンティニュの外部であれば、許可されない編集が認められる場合もあります。 そのような許可されない編集の結果を保持するには、デバッグを停止してアプリケーションを再起動する必要があります。  
  
 Windows 10 用の UWP アプリおよび .NET Framework 4.6 を対象とする x86 および x64 のアプリでエディット コンティニュはサポートされて (.NET Framework は、デスクトップのバージョンのみ) デスクトップまたはそれ以降のバージョン。

 > [!NOTE]
 > サポートされていないアプリとプラットフォームには、ASP.NET 5、Silverlight 5、および Windows 8.1 が含まれます。
  
 エディット コンティニュを使用してデバッグを開始するときはサポートされていない**プロセスにアタッチする**です。 エディット コンティニュはサポートされていません混在または最適化されたコードのマネージ コードとネイティブ コード。 詳細については、次を参照してください。[サポートされているコードの変更 (c# および Visual Basic](../debugger/supported-code-changes-csharp.md)です。
  
 このセクションの各トピックでは、この機能の使用方法と許可されない種類の変更について詳しく説明します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [方法 : エディット コンティニュの中断モード時に編集を適用する](../debugger/how-to-apply-edits-in-break-mode-with-edit-and-continue.md)  
 中断モードにおいてコードの編集を適用する方法について説明します。  
  
 [サポートされているコード変更 (c# および Visual Basic](../debugger/supported-code-changes-csharp.md)   
 [!INCLUDE[vb_current_short](../debugger/includes/vb_current_short_md.md)] エディット コンティニュで実行できない編集の種類について説明します。  
  
## <a name="related-sections"></a>関連項目  
 [エディット コンティニュ](../debugger/edit-and-continue.md)  
 エディット コンティニュに関するトピックの一覧を提供します。