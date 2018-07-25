---
title: プログラムの起動 |Microsoft Docs
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
ms.openlocfilehash: 5c56fd1c82c02428f9f6b67c1d715f1c61588858
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2018
ms.locfileid: "39231838"
---
# <a name="launch-a-program"></a>プログラムを起動します。
プログラムをデバッグする必要のあるユーザーがキーを押して**F5** IDE からデバッガーを実行します。 これには、一連の最終的に接続されている、または接続されているプログラムに次のようにさらにデバッグ エンジン (DE) への接続を IDE のイベントが開始されます。  
  
1.  IDE は、ソリューションのアクティブなプロジェクトのデバッグの設定を取得するプロジェクトのパッケージを最初に呼び出します。 設定には、開始ディレクトリ、環境変数、プログラムを実行するポートおよび指定されている場合に使用して、プログラムを作成する DE が含まれます。 これらの設定は、パッケージのデバッグに渡されます。  
  
2.  デが指定されている場合、DE、プログラムを起動するオペレーティング システムを呼び出します。 プログラムを起動するには、結果として、プログラムの実行時環境が読み込まれます。 たとえば、プログラムが MSIL で書き込まれた場合、プログラムを実行する共通言語ランタイムが呼び出されます。  
  
     - または -  
  
     デが指定されていない場合、ポートは、これにより、プログラムの実行時の環境を読み込むと、プログラムを起動するオペレーティング システムを呼び出します。  
  
    > [!NOTE]
    >  プログラムを起動する、DE を使用する場合は、同じ DE をプログラムにアタッチすることが高くなります。  
  
3.  かどうか、DE またはポートは、プログラムを起動することによって、DE または実行時環境プログラムの説明、またはノードを作成し、プログラムを実行しているポートを通知します。  
  
    > [!NOTE]
    >  プログラム ノードがデバッグ可能なプログラムの簡易表現であるために、実行時環境が、[プログラム] ノードを作成することをお勧めします。 作成し、[プログラム] ノードを登録するだけの全体の DE を読み込む必要はありません。 デが設計されている場合は、IDE が IDE のプロセスで実行するが実際に実行されている、ポートに、[プログラム] ノードを追加できるコンポーネントを使用する必要がありません。  
  
 他のすべてのプログラムと共に、新しく作成されたプログラムは、関連、関係のないまたは起動、または、同じ IDE からデバッグ セッションを作成する接続を。  
  
 プログラムでは、最初に押されたとき**F5**、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]のデバッグ パッケージがプロジェクト パッケージ (これに関連付けられた起動されるプログラムの種類) を呼び出しを通じて、<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.DebugLaunch%2A>メソッドで、順番に入力し、<xref:Microsoft.VisualStudio.Shell.Interop.VsDebugTargetInfo2>ソリューションのアクティブなプロジェクトのデバッグ設定を含む構造体。 この構造体に戻されるデバッグ パッケージを呼び出すことによって、<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebugger2.LaunchDebugTargets2%2A>メソッド。 パッケージのデバッグには、セッション デバッグ マネージャー (SDM) がデバッグし、関連するデバッグ エンジンをされているプログラムを起動し、インスタンス化します。  
  
 使用して、プログラムの起動を DE の GUID では、SDM に渡される引数のいずれか。  
  
 DE GUID がない場合`GUID_NULL`、SDM は併置、DE を作成しを呼び出してその[LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)メソッドは、プログラムを起動します。 たとえば、プログラムが、ネイティブ コードで記述された`IDebugEngineLaunch2::LaunchSuspended`が呼び出す可能性があります`CreateProcess`と`ResumeThread`(Win32 関数) をプログラムを実行します。  
  
 プログラムを起動するには、結果として、プログラムの実行時環境が読み込まれます。 デまたはランタイム環境を作成し、 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)プログラムを記述するインターフェイスし、このインターフェイスを渡します[AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)にポートがあるプログラムを通知するには実行中です。  
  
 場合`GUID_NULL`ポートがプログラムを起動し、渡されます。 実行時環境を作成、プログラムが実行されている、`IDebugProgramNode2`プログラムを記述するインターフェイスし、それを`IDebugPortNotify2::AddProgramNode`します。 これには、プログラムを実行しているポートに通知します。 SDM は、デバッグ エンジンを実行中のプログラムにアタッチします。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [ポートへの通知](../../extensibility/debugger/notifying-the-port.md)  
 プログラムが起動し、ポートの通知後の動作について説明します。  
  
 [起動後のアタッチ](../../extensibility/debugger/attaching-after-a-launch.md)  
 ドキュメント、デバッグ セッションが、DE をプログラムにアタッチする準備ができたときです。  
  
## <a name="related-sections"></a>関連項目  
 [タスクのデバッグ](../../extensibility/debugger/debugging-tasks.md)  
 プログラムを起動して、式の評価などのさまざまなデバッグ タスクへのリンクが含まれています。