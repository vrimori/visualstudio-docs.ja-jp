---
title: '方法: カスタム デバッグ エンジンのデバッグ |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, debugging
- debugging [Debugging SDK], custom debug engines
ms.assetid: df27a8d6-3938-45ff-b47f-b684e80b38a0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 95a2db2bc5e8990f536abc851941c337a1dee277
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-debug-a-custom-debug-engine"></a>方法: カスタム デバッグ エンジンをデバッグします。
プロジェクトの種類からのデバッグ エンジン (DE) の起動、<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.DebugLaunch%2A>メソッドです。 インスタンスの管理下にある、DE を起動するつまり[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]プロジェクトの種類を制御します。 ただし、そのインスタンスの[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]デをデバッグすることはできません。 以下は、カスタム、DE をデバッグできるようにする手順を示します。  
  
> [!NOTE]
>  :「デバッグはカスタム デバッグ エンジン」の手順では、添付する前に開始する DE を待つ必要があります。 メッセージ ボックス、DE の開始時に表示される、DE の先頭近くに配置する場合の点にアタッチし、引き続きメッセージ ボックスをオフにし、できます。 このように、キャッチできますすべて DE イベント。  
  
> [!WARNING]
>  次の手順を試行する前にインストールされているリモート デバッグが必要です。 参照してください[リモート デバッグ](../../debugger/remote-debugging.md)詳細についてはします。  
  
### <a name="debugging-a-custom-debug-engine"></a>カスタム デバッグ エンジンのデバッグ  
  
1.  Msvsmon.exe、リモート デバッグ モニターを起動します。  
  
2.  **ツール**msvsmon.exe、選択でメニュー**オプション**を開くには、**オプション** ダイアログ ボックス。  
  
3.  [認証なし] オプションを選択し、をクリックして**OK**です。  
  
4.  インスタンスを起動[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]カスタム DE プロジェクトを開きます。  
  
5.  2 番目のインスタンスを開始[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]デを起動するカスタム プロジェクトを開きます (開発では、これは、通常 VSIP がインストールされているときに設定されている、実験用のレジストリ ハイブで)。  
  
6.  この 2 つ目のインスタンスの[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]カスタム プロジェクトからソース ファイルを読み込み、およびデバッグするプログラムを起動します。 しばらく DE の読み込み、または、ブレークポイントがヒットするまでの待機に使用できるようにします。  
  
7.  最初のインスタンスで[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)](DE)、プロジェクトの次のように選択します。**プロセスにアタッチする**から、**デバッグ**メニュー。  
  
8.  **プロセスにアタッチする** ダイアログ ボックスで、変更、**トランスポート**に**リモート (認証なしのネイティブのみ)**です。  
  
9. 変更、**修飾子**コンピューターの名前に (注: エントリの履歴があるため、この名前に 1 回だけ入力する必要があります)。  
  
10. **選択可能なプロセス**一覧が実行中と をクリックする、DE のインスタンスを選択、**アタッチ**ボタンをクリックします。  
  
11. シンボルが読み込まれた後で、DE、DE コードでブレークポイントを設定します。  
  
12. 停止して、デバッグ プロセスを再起動するたびに、手順 6 ~ 10 を繰り返します。  
  
### <a name="debugging-a-custom-project-type"></a>カスタム プロジェクトの種類をデバッグ  
  
1.  開始[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]通常レジストリ ハイブおよび負荷でプロジェクトがプロジェクト (これは、プロジェクトの種類のインスタンス化ではない、プロジェクトの種類には、ソース) を入力します。  
  
2.  プロジェクトのプロパティを開きに移動、**デバッグ**ページ。 **コマンド**へのパスを入力、 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE (これは既定では、 *[ドライブ]*\Program Files\Microsoft [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 8\Common7\IDE\devenv.exe)。  
  
3.  **コマンド引数**、型`/rootsuffix exp`(VSIP のインストール時に作成される)、実験用レジストリ ハイブにします。  
  
4.  **[OK]** をクリックして変更内容を確定します。  
  
5.  F5 キーを押して、プロジェクトの種類を開始します。 2 番目のインスタンスが起動[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]です。  
  
6.  この時点では、プロジェクトの種類のソース コードにブレークポイントを配置できます。  
  
7.  2 番目のインスタンスで[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]読み込む、またはプロジェクトの種類の新しいインスタンスを作成します。 読み込みまたは作成中に、ブレークポイントがヒットする可能性があります。  
  
8.  プロジェクトの種類をデバッグします。  
  
9. デを起動するためのプロセスをデバッグする場合は、「デバッグはカスタム デバッグ エンジン」の手順の起動後に、DE にアタッチする手順を実行することができます。 これにより、3 つのインスタンス[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]を実行している: プロジェクト型のソース、インスタンスが作成されたプロジェクトの種類、および、DE にアタッチされている 3 つ目の 2 つ目のいずれか。  
  
## <a name="see-also"></a>関連項目  
 [カスタム デバッグ エンジンの作成](../../extensibility/debugger/creating-a-custom-debug-engine.md)