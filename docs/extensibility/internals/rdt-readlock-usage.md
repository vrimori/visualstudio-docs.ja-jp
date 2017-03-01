---
title: "RDT_ReadLock 使用 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- RDT_ReadLock
- visible
- RDT_EditLock
- invisible
ms.assetid: b935fc82-9d6b-4a8d-9b70-e9a5c5ad4a55
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: e7575b914f0645882f3570bdbe29221f2f8130cc
ms.openlocfilehash: a8ea44ef2dea3b3c4ebd29cf95b1886e2028e2c3
ms.lasthandoff: 02/22/2017

---
# <a name="rdtreadlock-usage"></a>RDT_ReadLock 使用状況

<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS>これは、Visual Studio IDE で現在開いているすべてのドキュメントの一覧を実行しているドキュメント テーブル (RDT)、ドキュメントをロックするためのロジックを提供するフラグです。</xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> このフラグは、ドキュメントを開いたとき、およびドキュメントは、ユーザー インターフェイスに表示するか非表示の状態をメモリに保持されているかどうかを決定します。

一般に、使用するよう<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS>が true で、次のいずれかの場合:</xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS>

- ドキュメントを目に見える開きたいときに読み取り専用ではまだ<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>それを所有</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>する確立が、

- ユーザーの前に視覚的に開かれているドキュメントの保存先の入力を要求するユーザーの場合、UI に表示しを閉じるには、試行します。

## <a name="how-to-manage-visible-and-invisible-documents"></a>ドキュメントの表示と非表示を管理する方法

UI では、ユーザーがドキュメントを開くときに、<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>ドキュメントの所有者を確立する必要があり、<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS>フラグを設定する必要があります</xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS></xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>。 ない場合<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>所有者が確立されると、そのユーザーがクリックすると、ドキュメントは保存されません**すべてを保存**か IDE を閉じます</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>。 かどうかは、ドキュメントが開いていない視覚的に、メモリで変更されていると、ユーザーがシャット ダウン時に、ドキュメントを保存するように求めまたは保存つまり**すべて保存**を選択した場合、`RDT_ReadLock`は使用できません。 代わりに、使用する必要があります、`RDT_EditLock`し、登録、<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder>ときに、<xref:Microsoft.VisualStudio.Shell.Interop.__VSREGDOCLOCKHOLDER>フラグ</xref:Microsoft.VisualStudio.Shell.Interop.__VSREGDOCLOCKHOLDER></xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder>。

## <a name="rdteditlock-and-document-modification"></a>RDT_EditLock とドキュメントの変更

前に記載されているフラグは、ドキュメントの非表示の開始が得られますことを示しますその`RDT_EditLock`に、参照できる、ユーザーが、文書が開かれたときに**ドキュメント ウィンドウ**です。 このような場合は、表示されます、**保存**求めるときに、表示可能**ドキュメント ウィンドウ**が閉じられます。 <xref:Microsoft.VisualStudio.Package.Automation.OAProject.CodeModel>使用する実装、<xref:Microsoft.VisualStudio.Shell.Interop.IVsInvisibleEditorManager>のみに最初に、サービスが動作する`RDT_ReadLock`(つまり、ドキュメントを開いたときにない視覚的に情報を解析する) に実行します</xref:Microsoft.VisualStudio.Shell.Interop.IVsInvisibleEditorManager>。</xref:Microsoft.VisualStudio.Package.Automation.OAProject.CodeModel> その後、ドキュメントを変更する必要がありますし、ロックにアップグレード、弱**RDT_EditLock**します。 ユーザーは、参照できるでドキュメントを開く場合**ドキュメント ウィンドウ**、`CodeModel`の弱い`RDT_EditLock`を解放します。

ユーザーが、終了した場合、**ドキュメント ウィンドウ**は選択**なし**、開いているドキュメントを保存するように求められたら、`CodeModel`実装は、ドキュメント内のすべての情報を破棄して、ドキュメントが開かれたいないディスクから視覚的に、次回の詳細については、ドキュメントに必要なです。 この動作の細部は、ユーザーが開いたインスタンス、**ドキュメント ウィンドウ**の非表示の開いているドキュメントには、それを変更して閉じを選択し、**いいえ**ドキュメントを保存するように求められたらします。 この場合は、ドキュメントがある場合、`RDT_ReadLock`ドキュメントが実際に閉じられることと、変更されたドキュメント開いたままになり、メモリ内の非表示の状態をドキュメントを保存しないように、ユーザーが選択した場合でもです。

ドキュメントの非表示を開くには、弱が使用している場合`RDT_EditLock`、ユーザーが目に見える文書を開き、他のロックが保持されていない場合、そのロックが得られます。 ユーザーが閉じたとき、**ドキュメント ウィンドウ**は選択**いいえ**ドキュメントを保存するメッセージが表示されたら、ドキュメント閉じる必要がありますメモリからです。 つまり、非表示のクライアントは、このアイテムのみを追跡するために RDT イベントをリッスンする必要があります。 ドキュメントが必要になる、次に、ドキュメントを再開する必要があります。
