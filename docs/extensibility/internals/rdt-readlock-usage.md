---
title: 使用状況の RDT_ReadLock |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- RDT_ReadLock
- visible
- RDT_EditLock
- invisible
ms.assetid: b935fc82-9d6b-4a8d-9b70-e9a5c5ad4a55
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7fda2fbb4a4b03dff9d677d9c7581a4138d9fcf7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31131682"
---
# <a name="rdtreadlock-usage"></a>RDT_ReadLock の使用方法

<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> これは、Visual Studio IDE で現在開かれているすべてのドキュメントの一覧で、実行されているドキュメント テーブル (RDT)、ドキュメントをロックするためのロジックを提供するフラグ。 このフラグは、ドキュメントを開いたとき、およびドキュメントは、ユーザー インターフェイスで表示または非表示の状態をメモリに保持されているかどうかを判断します。

一般に、使用するよう<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS>次のいずれかが true の場合。

- 視覚的に文書を開いたりする場合、読み取り専用とがまだ確立するが、<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>自分が所有する必要があります。

- 場合、ユーザーを視覚的に開かれたいないユーザーが UI に表示され、再を閉じるには試行する前にドキュメントを保存するように求められます。

## <a name="how-to-manage-visible-and-invisible-documents"></a>表示と非表示のドキュメントを管理する方法

ユーザーが UI では、ドキュメントを開いたときに、<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>ドキュメントの所有者を確立する必要がありますと<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS>フラグを設定する必要があります。 ない場合は<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>所有者が確立されると、そのユーザーがクリックしたときに、ドキュメントは保存されません**すべてを保存**か IDE を閉じます。 かどうか、ドキュメントが開いていない視覚的にメモリで変更されているし、ユーザーがシャット ダウン時にドキュメントを保存するように求めまたは保存された場合、つまり**すべて保存**を選択した場合、`RDT_ReadLock`は使用できません。 代わりに、使用する必要があります、`RDT_EditLock`を登録し、<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder>ときに、<xref:Microsoft.VisualStudio.Shell.Interop.__VSREGDOCLOCKHOLDER>フラグ。

## <a name="rdteditlock-and-document-modification"></a>RDT_EditLock とドキュメントの変更

示されている前のフラグは、ドキュメントの非表示の開始を生成することを示します、`RDT_EditLock`ときに、ドキュメントを開いたユーザーの表示に**ドキュメント ウィンドウ**します。 ユーザーに提示は、このエラーが発生、**保存**求めるときに、表示可能**ドキュメント ウィンドウ**が閉じられます。 `Microsoft.VisualStudio.Package.Automation.OAProject.CodeModel` 使用する実装、<xref:Microsoft.VisualStudio.Shell.Interop.IVsInvisibleEditorManager>のみに最初に、サービスが動作、`RDT_ReadLock`は (つまり、ドキュメントを開いたときにない視覚的に情報を解析する) を取得します。 後で、ドキュメントを変更する必要があります、し、ロックにアップグレード、弱**RDT_EditLock**です。 ユーザーは、表示で、ドキュメントを開く場合**ドキュメント ウィンドウ**、`CodeModel`の弱い`RDT_EditLock`を解放します。

ユーザーが、終了した場合、**ドキュメント ウィンドウ**は選択**いいえ**、開いているドキュメントを保存するように求められたら、`CodeModel`実装が、ドキュメント内のすべての情報を破棄して、再度開かれます、非表示の状態、次回の詳細については、ドキュメントに必要なディスクからのドキュメントです。 この動作の細部が、ユーザーが開くインスタンス、**ドキュメント ウィンドウ**非表示の開いているドキュメントの変更が閉じるし、選択**いいえ**ドキュメントを保存するように求められたらです。 ここでは、ドキュメントがある場合、`RDT_ReadLock`ドキュメントは実際に閉じられましていないと、変更されたドキュメントは開いたまま、メモリの非表示の状態でユーザーがドキュメントを保存しないように選択した場合でもです。

ドキュメントの非表示を開くには、弱が使用している場合`RDT_EditLock`、ユーザーが視覚的に文書を開き、他のロックが保持されていないときに、そのロックが得られます。 ユーザーが閉じたとき、**ドキュメント ウィンドウ**は選択**いいえ**ドキュメントを保存するメッセージが表示されたら、ドキュメント閉じる必要がありますメモリからです。 つまり、非表示のクライアントは、このアイテムのみを追跡するために RDT イベントをリッスンする必要があります。 次回、ドキュメントが必要ですが、ドキュメントを再開する必要があります。