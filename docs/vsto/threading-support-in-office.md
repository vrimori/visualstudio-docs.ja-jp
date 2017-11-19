---
title: "スレッド処理の Office でサポート |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- multiple threads [Office development in Visual Studio]
- threading [Office development in Visual Studio]
- Office applications [Office development in Visual Studio], threading support
- object models [Office development in Visual Studio], threading support
ms.assetid: 810a6648-fece-4b43-9eb6-948d28ed2157
caps.latest.revision: "33"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: bbfccabe310732943a818515c69abc61bec59e52
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="threading-support-in-office"></a>Office でのスレッドのサポート
  このトピックでは、Microsoft Office オブジェクト モデルのスレッド処理のサポートについての情報を提供します。 Office オブジェクト モデルは、スレッド セーフではありませんが、Office ソリューションで複数のスレッドを使用することです。 Office アプリケーションは、コンポーネント オブジェクト モデル (COM) サーバーです。 COM には、クライアントは任意のスレッドの COM サーバーを呼び出すことができます。 COM サーバーのスレッド セーフではない場合は、COM は、1 つだけの論理スレッドがいつでも、サーバーで実行されるように、同時呼び出し数をシリアル化するためのメカニズムを提供します。 このメカニズムは、シングル スレッド アパートメント (STA) モデルと呼ばれます。 呼び出しは、シリアル化されるための呼び出し元がブロックされている期間、サーバーがビジー状態か、バック グラウンド スレッドでその他の呼び出しが処理中にします。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="knowledge-required-when-using-multiple-threads"></a>複数のスレッドを使用する場合に必要な知識  
 複数のスレッドを使用する次の要素の少なくとも基本的な知識が必要するマルチ スレッド。  
  
-   Windows Api  
  
-   COM マルチ スレッドの概念  
  
-   同時実行  
  
-   同期  
  
-   マーシャ リング  
  
 一般的な情報については別に分けたりを参照してください[マネージ スレッド処理](/dotnet/standard/threading/)です。  
  
 Office はメイン STA で実行されます。 この影響を理解できるようになります Office で複数のスレッドを使用する方法を理解します。  
  
## <a name="basic-multithreading-scenario"></a>マルチ スレッド処理の基本的なシナリオ  
 Office ソリューションのコードは、常に、メイン UI スレッドで実行されます。 バック グラウンド スレッドで個別のタスクを実行して、アプリケーションのパフォーマンスを滑らかにする可能性があります。 目標は、タスクを実行する 2 つ一見同時円滑に実行 (複数のスレッドを使用する主な理由) になりますが、後、その他の 1 つのタスクではなくです。 たとえば、メインの Excel の UI スレッドで、イベントのコードがある可能性があり、バック グラウンド スレッドでは、サーバーからデータを収集し、サーバーからのデータと Excel の UI 内のセルを更新するタスクを実行する可能性があります。  
  
## <a name="background-threads-that-call-into-the-office-object-model"></a>Office オブジェクト モデルへの呼び出しをバック グラウンド スレッド  
 バック グラウンド スレッド、Office アプリケーションを呼び出すとき、呼び出しが自動的に STA の境界を越えてマーシャ リングします。 ただし、Office アプリケーションがバック グラウンド スレッドになります、時に呼び出しを処理できることを保証することはありません。 これにはいくつかの可能性があります。  
  
1.  Office アプリケーションでは、入力する機会を得るための呼び出しのメッセージをポンプする必要があります。 これには場合、処理が明け渡さこれには時間がかかります。  
  
2.  別の論理スレッド アパートメント内では既に、新しいスレッドは入力できません。 これは、論理的なスレッドは、Office アプリケーションを入力し、後、再入可能呼び出しを呼び出し元のアパートメントに戻す場合によく発生します。 その呼び出しが戻るを待って、アプリケーションがブロックされます。  
  
3.  Excel は、着信呼び出しをすぐに処理できないように、状態である可能性があります。 たとえば、Office アプリケーションはモーダル ダイアログ ボックスを表示している可能性があります。  
  
 2 および 3 を可能にする COM が用意されており、 [IMessageFilter](http://msdn.microsoft.com/en-us/e12d48c0-5033-47a8-bdcd-e94c49857248)インターフェイスです。 すべての呼び出しが入力、サーバーを実装すると場合、[がこのインターフェイス](http://msdn.microsoft.com/en-us/7e31b518-ef4f-4bdd-b5c7-e1b16383a5be)メソッドです。 考慮事項 2 では、呼び出しが自動的に拒否されます。 3 考慮事項は、サーバーは、状況によって、呼び出しを拒否できます。 呼び出しが拒否された場合、呼び出し元は、必要があります処理を決定します。 呼び出し元の実装では通常、 [IMessageFilter](http://msdn.microsoft.com/en-us/e12d48c0-5033-47a8-bdcd-e94c49857248)、後者によって、却下の通知とする、 [RetryRejectedCall](http://msdn.microsoft.com/en-us/3f800819-2a21-4e46-ad15-f9594fac1a3d)メソッドです。  
  
 ただし、Visual Studio の Office 開発ツールを使用して作成されたソリューションを場合 COM 相互運用変換、拒否されたすべての呼び出し、 <xref:System.Runtime.InteropServices.COMException> ("メッセージ フィルターによる、アプリケーションがビジー状態である") です。 オブジェクト モデルを呼び出すを加えるたびにバック グラウンド スレッドでは、この例外を処理する準備する必要があります。 通常、関連する一定の時間の再試行およびダイアログを表示します。 ただしも STA としてバック グラウンド スレッドを作成し、このケースを処理するには、そのスレッドのメッセージ フィルターを登録できます。  
  
## <a name="starting-the-thread-correctly"></a>正しくスレッドの起動  
 新しい STA スレッドを作成するときに、スレッドを開始する前に、sta アパートメント状態を設定します。 これを実行する方法を次のコード例に示します。  
  
 [!code-csharp[Trin_VstcoreCreatingExcel#5](../vsto/codesnippet/CSharp/Trin_VstcoreCreatingExcelCS/ThisWorkbook.cs#5)]
 [!code-vb[Trin_VstcoreCreatingExcel#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreCreatingExcelVB/ThisWorkbook.vb#5)]  
  
 詳細については、次を参照してください。[マネージ スレッド処理の実施](/dotnet/standard/threading/managed-threading-best-practices)です。  
  
## <a name="modeless-forms"></a>モードレスのフォーム  
 モードレスのフォームでは、フォームが表示されている間に何らかの種類のアプリケーションとの対話ができます。 フォームをユーザーが操作して、フォームは閉じずに、アプリケーションによって対話します。 Office オブジェクト モデルがマネージ モードレス フォーム; をサポートしていますただし、これら指定しないでバック グラウンド スレッドでします。  
  
## <a name="see-also"></a>関連項目  
 [マネージ スレッド処理](/dotnet/standard/threading/)  
 [スレッド処理 (c#)](/dotnet/csharp/programming-guide/concepts/threading/index) [スレッド処理 (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/threading/index)   
 [スレッドの使用とスレッド処理](/dotnet/standard/threading/using-threads-and-threading)   
 [Office ソリューションのデザインと作成](../vsto/designing-and-creating-office-solutions.md)  
  
  