---
title: "方法: カスタム デバッグ エンジンをデバッグします。 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "デバッグ エンジンは、デバッグ"
  - "[デバッグ SDK] カスタム デバッグ エンジンのデバッグ"
ms.assetid: df27a8d6-3938-45ff-b47f-b684e80b38a0
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# 方法: カスタム デバッグ エンジンをデバッグします。
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

プロジェクトの種類は <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.DebugLaunch%2A> のメソッドから \(DE\) デバッグ エンジンを起動します。  これはde\-DEプロジェクトの種類を制御する [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] のインスタンスの制御下で起動することを意味します。  ただし[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] のインスタンスは de\-DE はデバッグできません。  DE 従ってカスタムのデバッグに使用できるステップがあります。  
  
> [!NOTE]
>  :     「デバッグ カスタムのデバッグ エンジンではアタッチするには」の手順を実行するにはde\-DE を待機する必要があります。  DE 次にを起動したときに表示される DE の先頭付近にメッセージ ボックスをオフにすると次のメッセージ ボックス場合にアタッチできます。  このようにするとすべての de\-DE events をキャッチできます。  
  
> [!WARNING]
>  次の手順を実行する前にリモート デバッグをインストールする必要があります。  詳細については、「[リモート デバッグ](../../debugger/remote-debugging.md)」を参照してください。  
  
### カスタムのデバッグ エンジンのデバッグ  
  
1.  開始のリモート デバッグ モニター \(msvsmon.exe。  
  
2.  msvsmon.exe の ENT0ENT \[入力\] メニューの \[ENT3ENT\] ダイアログ ボックスを開くに ENT1ENT \[\] を選択します。  
  
3.  「 Authentication 」オプションを選択せずENT0ENT \[\] をクリックします。  
  
4.  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] のインスタンスを起動しカスタム DE プロジェクトを開きます。  
  
5.  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] の第 2 インスタンスを起動しde\-DE を起動するカスタム プロジェクトを開きます \(開発の場合セットアップ実験レジストリ ハイブに VSIP がインストールされている場合\)通常になります。  
  
6.  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] の 2 番目のインスタンスでカスタム プロジェクトのソース ファイルを読み込んでデバッグするプログラムを起動します。  DE を読み込む少数の時刻を待機するかブレークポイントにヒットするまで待ちます。  
  
7.  最初に [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] \(de\-DE\) プロジェクトとENT4ENT \[入力\] メニューの \[ENT2ENT\] を選択します。  
  
8.  \[入力\] ENT0ENT ダイアログ ボックスで **リモート \(認証なしのネイティブのみ\)** に  **トランスポート**  を変更します。  
  
9. コンピューター \(メモの名前に  **修飾子**  を : エントリの履歴があるため一度だけこの名前を入力する必要があります\)。  
  
10. \[入力\] ENT0ENT リストではが実行されている選択し\[ENT1ENT\] ボタンをクリックしのインスタンスをします。  
  
11. DE でシンボルを読み込んだ後de\-DE コードにブレークポイントを設定します。  
  
12. デバッグ プロセスを停止し再起動するたびに手順 6 ~ 10. を繰り返します。  
  
### カスタム プロジェクトをデバッグ  
  
1.  正常なレジストリ ハイブの [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] を起動しプロジェクトの種類のプロジェクトを読み込みます。これはソース プロジェクトの種類のプロジェクトの種類にインスタンス化できます\)。  
  
2.  プロジェクトのプロパティを開き\[入力\] ENT0ENT のページに移動します。   **コマンド**  については[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE のパスを入力します \(既定ではこれは  *ドライブ \[入力\]*\\ Program Files \\ Microsoft [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 8 \\ Common7 \\ IDE \\ devenv.exe " になります\)。  
  
3.  **コマンド引数**  の場合VSIP\) のインストール時にもレジストリ ハイブの型 \(`/rootsuffix exp` 作成します。  
  
4.  **\[OK\]** をクリックして、変更を適用します。  
  
5.  F5 キーを押してプロジェクトを実行します。  これは [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] の第 2 インスタンスを起動します。  
  
6.  この時点でプロジェクトのソース・コードにブレークポイントを設定できます。  
  
7.  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] の 2 番目のインスタンスでプロジェクトの種類の新しいインスタンスを読み込むか作成します。  ロード テストまたは作成時にブレークポイントはヒットする場合があります。  
  
8.  プロジェクトをデバッグします。  
  
9. DE を起動するプロセスをデバッグすると起動したら de\-DE にアタッチしたりカスタムのデバッグ エンジン 「 Debug 」の手順の手順を実行します。  これは [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] の実行に 3 個のインスタンスがあります : インスタンス化されたプロジェクトの種類のプロジェクトのソース秒および de\-DE にアタッチされている番目の 1 つがあります。  
  
## 参照  
 [カスタム デバッグ エンジンを作成します。](../../extensibility/debugger/creating-a-custom-debug-engine.md)