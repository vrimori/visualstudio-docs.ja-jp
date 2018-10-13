---
title: '方法: カスタム デバッグ エンジンのデバッグ |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debug engines, debugging
- debugging [Debugging SDK], custom debug engines
ms.assetid: df27a8d6-3938-45ff-b47f-b684e80b38a0
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1e1bd7e2c3f05fd54829d042ec15fd59b783d238
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49247235"
---
# <a name="how-to-debug-a-custom-debug-engine"></a>方法: カスタム デバッグ エンジンのデバッグ
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

プロジェクトの種類からのデバッグ エンジン (DE) の起動、<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.DebugLaunch%2A>メソッド。 つまりのインスタンスの管理下にある、DE を起動する[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]プロジェクトの種類を制御します。 ただし、そのインスタンスの[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]DE をデバッグすることはできません。 どのような次のようには、カスタム、DE をデバッグすることを許可する手順を示します。  
  
> [!NOTE]
>  :「デバッグをカスタム デバッグ エンジン」の手順では、添付する前に開始するを待つ必要があります。 メッセージ ボックス、DE の開始時に表示される、ドイツの先頭近くに配置する場合は、その時点でアタッチし、引き続きメッセージ ボックスをオフにし。 そうすることを検出できますすべて DE イベント。  
  
> [!WARNING]
>  次の手順を試行する前にインストールされているリモート デバッグが必要です。 参照してください[リモート デバッグ](../../debugger/remote-debugging.md)詳細についてはします。  
  
### <a name="debugging-a-custom-debug-engine"></a>カスタム デバッグ エンジンのデバッグ  
  
1.  Msvsmon.exe、リモート デバッグ モニターを起動します。  
  
2.  **ツール**で msvsmon.exe を選択します メニューの **オプション**を開く、**オプション** ダイアログ ボックス。  
  
3.  [認証なし] オプションを選択し、クリックして**OK**します。  
  
4.  インスタンスを起動[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]カスタム DE プロジェクトを開きます。  
  
5.  2 番目のインスタンスを開始[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]DE を起動するカスタム プロジェクトを開くと (開発、これは通常 VSIP のインストール時に設定されている実験用のレジストリ ハイブに)。  
  
6.  この 2 番目のインスタンスで[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]、カスタム プロジェクトからソース ファイルを読み込み、およびデバッグするプログラムを起動します。 しばらく読み込み、または、ブレークポイントにヒットするまで待機する DE を許可するを待機します。  
  
7.  最初のインスタンスで[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)](DE プロジェクト) と選択**プロセスにアタッチ**から、**デバッグ**メニュー。  
  
8.  **プロセスにアタッチ** ダイアログ ボックスで、変更、**トランスポート**に**リモート (認証なしのネイティブのみ)** します。  
  
9. 変更、**修飾子**コンピューターの名前に (注: この名前に 1 回だけ入力する必要があるため、エントリの履歴がある)。  
  
10. **選択可能なプロセス**一覧を実行し、DE のインスタンスを選択、**アタッチ**ボタンをクリックします。  
  
11. DE でシンボルが読み込まれた後は、DE コードにブレークポイントを設定します。  
  
12. 停止して、デバッグ プロセスを再起動するたびに、手順 6 ~ 10 を繰り返します。  
  
### <a name="debugging-a-custom-project-type"></a>カスタム プロジェクトの種類をデバッグします。  
  
1.  開始[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]プロジェクトは、通常のレジストリ ハイブと負荷のプロジェクト (これは、ソースのプロジェクトの種類、プロジェクトの種類のインスタンス化ではありません) を入力します。  
  
2.  プロジェクトのプロパティを開きに移動、**デバッグ**ページ。 **コマンド**へのパスを入力、 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE (これは、既定では、 *[ドライブ]* \Program Files\Microsoft [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 8\Common7\IDE\devenv.exe)。  
  
3.  **コマンド引数**、型`/rootsuffix exp`(VSIP のインストール時に作成された) 実験用のレジストリ ハイブ。  
  
4.  **[OK]** をクリックして変更内容を確定します。  
  
5.  F5 キーを押して、プロジェクトの種類を開始します。 2 番目のインスタンスが起動[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]します。  
  
6.  この時点で、プロジェクトの種類のソース コードにブレークポイントを配置できます。  
  
7.  2 番目のインスタンスで[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]、読み込みまたはプロジェクトの種類の新しいインスタンスを作成します。 読み込みまたは作成中に、ブレークポイントがヒットする可能性があります。  
  
8.  プロジェクトの種類をデバッグします。  
  
9. DE を起動するためのプロセスをデバッグする場合は、起動された後、DE にアタッチする「デバッグをカスタム デバッグ エンジン」の手順で、手順を実行できます。 3 つのインスタンスを提供[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]を実行している: プロジェクト型のソースをインスタンス化されたプロジェクトの種類と、DE にアタッチされている 3 つ目の 2 つ目の 1 つ。  
  
## <a name="see-also"></a>関連項目  
 [カスタム デバッグ エンジンの作成](../../extensibility/debugger/creating-a-custom-debug-engine.md)

