---
title: スレッドの Office でのサポート
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- multiple threads [Office development in Visual Studio]
- threading [Office development in Visual Studio]
- Office applications [Office development in Visual Studio], threading support
- object models [Office development in Visual Studio], threading support
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: f5c2a0a8623228091e2acee184fa0272c2bbf311
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2018
ms.locfileid: "37059260"
---
# <a name="threading-support-in-office"></a>スレッドの Office でのサポート
  この記事では、Microsoft Office オブジェクト モデルのスレッド処理のサポートについての詳細についての情報を提供します。 Office オブジェクト モデルは、スレッド セーフではありませんが、Office ソリューションで複数のスレッドを使用することは。 Office アプリケーションは、コンポーネント オブジェクト モデル (COM) サーバーです。 COM は、任意のスレッド上の COM サーバーを呼び出すクライアントを許可します。 COM サーバーのスレッド セーフではない場合は、COM は、1 つの論理スレッドがいつでも、サーバーで実行できるように、同時呼び出しをシリアル化するためのメカニズムを提供します。 このメカニズムは、シングル スレッド アパートメント (STA) モデルと呼ばれます。 呼び出しはシリアル化するため、サーバーがビジー状態またはバック グラウンド スレッドでその他の呼び出しが処理中に呼び出し元は時間にわたってブロック可能性があります。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="knowledge-required-when-using-multiple-threads"></a>複数のスレッドを使用する場合に必要な知識  
 複数のスレッドを使用する必要がありますの次の側面について少なくとも基本的な知識があるマルチ スレッド。  
  
-   Windows Api  
  
-   COM マルチ スレッドの概念  
  
-   同時実行  
  
-   同期  
  
-   マーシャ リング  
  
 一般的な情報についてのマルチ スレッドを参照してください[マネージ スレッド処理](/dotnet/standard/threading/)します。  
  
 Office はメイン STA で実行されます。 この機能の影響を理解できるようになります Office で複数のスレッドを使用する方法を理解します。  
  
## <a name="basic-multithreading-scenario"></a>基本的なマルチ スレッド シナリオ  
 Office ソリューションのコードは、常に、メイン UI スレッドで実行されます。 バック グラウンド スレッドで別のタスクを実行して、アプリケーションのパフォーマンスを滑らかにすることがあります。 目標は、タスクを実行する 2 つ一見一度に円滑に実行 (複数のスレッドを使用する主な理由) にする必要があります、続けて、別の 1 つのタスクではなくです。 たとえば、メインの Excel の UI スレッドで、イベントのコードがあり、バック グラウンド スレッドでは、サーバーからデータを収集し、サーバーからデータを Excel UI 内のセルを更新するタスクを実行する可能性があります。  
  
## <a name="background-threads-that-call-into-the-office-object-model"></a>Office オブジェクト モデルを呼び出すバック グラウンド スレッド  
 バック グラウンド スレッドが、Office アプリケーションへの呼び出しを行うと、呼び出しが自動的に STA の境界を越えてマーシャ リングします。 ただし、Office アプリケーションがバック グラウンド スレッドになります、時に呼び出しを処理できるという保証はありません。 これにはいくつかの可能性があります。  
  
1.  Office アプリケーションでは、呼び出しを入力する機会を得るためのメッセージをポンプする必要があります。 これには場合、処理が明け渡さこれには時間がかかります。  
  
2.  別の論理スレッド アパートメント内では既に、新しいスレッドは入力できません。 これは多くの場合、論理スレッドが Office アプリケーションに入った後、再入可能呼び出しを呼び出し元のアパートメントに戻す場合に発生します。 その呼び出しが戻るを待機しているアプリケーションがブロックされます。  
  
3.  Excel は、着信通話をすぐに処理できないように、状態である可能性があります。 たとえば、Office アプリケーションには、モーダル ダイアログを表示可能性があります。  
  
 2 および 3 の可能性について、 [IMessageFilter](/windows/desktop/api/objidl/nn-objidl-imessagefilter)インターフェイス。 を通じて場合は、サーバーを実装すると、すべての呼び出しを入力してください、[がこのインターフェイス](/windows/desktop/api/objidl/nf-objidl-imessagefilter-handleincomingcall)メソッド。 2 考慮事項は、呼び出しは自動的に拒否されます。 3 考慮事項は、サーバーは、状況に応じて、呼び出しを拒否できます。 呼び出しが拒否された場合、呼び出し元は対処方法を決定する必要があります。 呼び出し元の実装では通常、 [IMessageFilter](/windows/desktop/api/objidl/nn-objidl-imessagefilter)、によって拒否されたの通知では、 [RetryRejectedCall](/windows/desktop/api/objidl/nf-objidl-imessagefilter-retryrejectedcall)メソッド。  
  
 ただし、場合は、Visual Studio の Office 開発ツールを使用して作成されたソリューションでは、COM 相互運用機能変換、拒否されたすべての呼び出しを<xref:System.Runtime.InteropServices.COMException>(「メッセージ フィルター示される、アプリケーションがビジー状態である」)。 オブジェクト モデルを呼び出すを加えるたびに、バック グラウンド スレッドでこの例外を処理する準備をする必要があります。 通常、一定の時間の再試行と、ダイアログを表示する必要があります。 ただしも STA としてバック グラウンド スレッドを作成し、このケースを処理するには、そのスレッドのメッセージ フィルターを登録できます。  
  
## <a name="start-the-thread-correctly"></a>スレッドが正常に起動します。  
 新しい STA スレッドを作成するときに、スレッドを開始する前に、sta アパートメント状態を設定します。 これを実行する方法を次のコード例に示します。  
  
 [!code-csharp[Trin_VstcoreCreatingExcel#5](../vsto/codesnippet/CSharp/Trin_VstcoreCreatingExcelCS/ThisWorkbook.cs#5)]
 [!code-vb[Trin_VstcoreCreatingExcel#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreCreatingExcelVB/ThisWorkbook.vb#5)]  
  
 詳細については、次を参照してください。[マネージ スレッド処理のベスト プラクティス](/dotnet/standard/threading/managed-threading-best-practices)します。  
  
## <a name="modeless-forms"></a>モードレス フォーム  
 モードレス フォームでは、フォームが表示されている間に何らかの種類のアプリケーションとの対話ができます。 ユーザーが、フォームとやり取りし、フォームが閉じることがなくアプリケーションを操作します。 Office オブジェクト モデルには、管理対象のモードレス フォーム; がサポートされていますただしが使用できない場合がバック グラウンド スレッドでします。  
  
## <a name="see-also"></a>関連項目  
 [マネージ スレッド処理](/dotnet/standard/threading/)  
 [スレッド処理 (c#)](/dotnet/csharp/programming-guide/concepts/threading/index) [スレッド処理 (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/threading/index)   
 [使用してスレッドおよびスレッド処理](/dotnet/standard/threading/using-threads-and-threading)   
 [設計および Office ソリューションの作成](../vsto/designing-and-creating-office-solutions.md)  
  
  