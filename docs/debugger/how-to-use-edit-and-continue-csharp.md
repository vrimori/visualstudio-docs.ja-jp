---
title: '方法: エディット コンティニュを使用 (c#) |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue [C#], about Edit and Continue
ms.assetid: 40e136d8-a08c-43bd-b313-fb821c55eb3c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 587ee3bb7221c0fce82048112945ac8581796d23
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-use-edit-and-continue-c"></a>方法 : エディット コンティニュを使用する (C#)
C# のエディット コンティニュを使用すると、デバッグ中に中断モードでコードに変更を加えることができます。 デバッグ セッションを停止したり再開したりしなくても、変更を適用できます。  
  
 エディット コンティニュは自動的に呼び出される、中断モードで変更を行い、デバッガーの実行を選択するときにコマンドなど、**続行**、**ステップ**、または**次のステートメントの設定**、か、デバッガー ウィンドウで関数を評価します。  
  
> [!NOTE]
>  最適化されたコード、ネイティブ/マネージ混合コード、または SQL Server 共通言語ランタイム (CLR) 統合コードをデバッグするときに、エディット コンティニュのサポートはされていません。 サポートされていないその他のシナリオについては、次を参照してください。 [(c# および Visual Basic) のサポートされているコード変更](../debugger/supported-code-changes-csharp.md)です。 これらのシナリオでは、デバッガーが表示されますが、ダイアログ ボックスについて詳しく説明するエディット コンティニュはサポートされていませんのいずれかでコード変更を適用しようとするとします。  
  
### <a name="to-invoke-edit-and-continue-automatically"></a>エディット コンティニュを自動的に呼び出すには  
  
1.  中断モードで、ソース コードを変更します。  
  
2.  **デバッグ** メニューのをクリックして**続行**、**ステップ**、または**次のステートメントの設定**か、デバッガー ウィンドウで関数を評価します。  
  
     新しいコードがコンパイルされ、その新しいコードでデバッグが続行されます。 エディット コンティニュでサポートされない変更もあります。 詳細については、次を参照してください。 [(c# および Visual Basic) のサポートされているコード変更](../debugger/supported-code-changes-csharp.md)です。  
  
### <a name="to-enabledisable-edit-and-continue"></a>[エディット コンティニュ] を有効または無効にするには  
  
1.  **[ツール]** メニューの **[オプション]**をクリックします。  
  
2.  **オプション** ダイアログ ボックスで、展開、**デバッグ**ノード、および選択**エディット コンティニュ**です。  
  
3.  **オプション**] ダイアログ ボックス**エディット コンティニュ**ページ、オンまたはオフ、 **[エディット コンティニュ**チェック ボックスをオンします。  
  
     デバッグ セッションを再開すると、この設定が有効になります。  
  
## <a name="see-also"></a>関連項目  
 [エディット コンティニュ (Visual c#)](../debugger/edit-and-continue-visual-csharp.md)   
 [サポートされているコード変更 (c# および Visual Basic)](../debugger/supported-code-changes-csharp.md)   