---
title: プログラムを起動 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, launching
- programs, launching
ms.assetid: 6857e9c6-e44a-468a-afa4-f7c4a0b77844
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 714d751e9855b5567bf76ccd902fada727e14ba1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="launching-a-program"></a>プログラムの起動
プログラムをデバッグするユーザーは、IDE からデバッガーを実行する f5 キーを押してことができます。 これは、一連の最終的には、IDE がさらに接続されている、または、プログラムに添付された、次のようにされているデバッグ エンジン (DE) に接続すると、イベントを開始します。  
  
1.  IDE 最初パッケージを呼び出して、プロジェクト、ソリューションのアクティブなプロジェクトのデバッグ設定を取得します。 設定には、開始ディレクトリ、環境変数、ポート、プログラムを実行する、および指定した場合に使用して、プログラムを作成する DE が含まれます。 これらの設定は、デバッグ パッケージに渡されます。  
  
2.  デが指定されている場合、DE、プログラムを起動するオペレーティング システムを呼び出します。 プログラムを起動するには、結果として、プログラムの実行時環境が読み込まれます。 たとえば、プログラムが MSIL で書き込まれた場合、プログラムを実行する共通言語ランタイムは呼び出されます。  
  
     - または -  
  
     デが指定されていない場合、ポートは、これにより、プログラムの実行時環境に読み込まれると、プログラムを起動するオペレーティング システムを呼び出します。  
  
    > [!NOTE]
    >  デを使用するプログラムを起動すると、その同じ DE がプログラムに接続する可能性があります。  
  
3.  かどうか、DE またはポートは、プログラムを起動、によって、DE または実行時環境プログラムの説明、またはノードを作成し、プログラムを実行しているポートに通知します。  
  
    > [!NOTE]
    >  プログラム ノードはデバッグ可能なプログラムの簡易表現であるために、実行時環境が、[プログラム] ノードを作成することをお勧めします。 作成して、[プログラム] ノードを登録するだけの全体の DE をロードする必要はありません。 デが設計されている場合、IDE が IDE プロセス内で実行する実際に実行して、ポートに、[プログラム] ノードを追加できるコンポーネントを使用する必要がありません。  
  
 他のすべてのプログラムと共に、新しく作成されたプログラム関連関係のない、起動または同じの IDE からデバッグ セッションを作成する接続します。  
  
 プログラムでは、最初に押されたとき**f5 キーを押して**、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]のデバッグ パッケージが (関連付けられているプログラムの起動の型と)、プロジェクト パッケージを呼び出してから、<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.DebugLaunch%2A>をさらに記入するメソッドを<xref:Microsoft.VisualStudio.Shell.Interop.VsDebugTargetInfo2>ソリューションのアクティブなプロジェクトのデバッグ設定を含む構造体。 この構造体に返されるデバッグ パッケージを呼び出すことによって、<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebugger2.LaunchDebugTargets2%2A>メソッドです。 デバッグ パッケージには、セッション デバッグ マネージャー (SDM) がデバッグし、関連するデバッグ エンジンをされているプログラムを起動し、インスタンス化します。  
  
 プログラムを起動するために使用する DE の GUID では、SDM に渡された引数のいずれか。  
  
 DE GUID がない場合`GUID_NULL`、SDM が併置、DE を作成しを呼び出してその[LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)プログラムを起動する方法です。 たとえば、プログラムは、ネイティブ コードで記述`IDebugEngineLaunch2::LaunchSuspended`が呼び出す可能性があります`CreateProcess`と`ResumeThread`(Win32 関数) をプログラムを実行します。  
  
 プログラムを起動するには、結果として、プログラムの実行時環境が読み込まれます。 デか、実行時環境を作成し、 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)プログラムを記述するインターフェイスし、このインターフェイスを通過[AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)ポートがあるプログラムに通知するには実行中です。  
  
 場合`GUID_NULL`渡されると、ポートは、プログラムを起動します。 プログラムが実行されていると、ランタイム環境を作成、`IDebugProgramNode2`プログラムを記述するインターフェイスし、に渡します`IDebugPortNotify2::AddProgramNode`です。 これにより、プログラムを実行しているポートが通知されます。 SDM はデバッグ エンジンを実行中のプログラムにアタッチします。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [ポートへの通知](../../extensibility/debugger/notifying-the-port.md)  
 プログラムが起動され、ポートの通知後の動作について説明します。  
  
 [起動後のアタッチ](../../extensibility/debugger/attaching-after-a-launch.md)  
 ドキュメント、デバッグ セッションは、プログラムに、DE をアタッチする準備ができます。  
  
## <a name="related-sections"></a>関連項目  
 [タスクのデバッグ](../../extensibility/debugger/debugging-tasks.md)  
 プログラムを起動して、式を評価するなど、さまざまなデバッグ タスクへのリンクが含まれています。