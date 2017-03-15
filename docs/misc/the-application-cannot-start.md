---
title: "The application cannot start. | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.message.0x800A0001"
  - "vs.message.VB_E_IDACANTBOOT"
ms.assetid: ffc123a0-99e1-4e9d-8f6e-34aa357bf98f
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# The application cannot start.
予期しないエラーが発生したため、Visual Studio を起動できませんでした。  このエラーは、次のいずれかの状況に該当する場合に発生します。  
  
-   統合開発環境 \(IDE\) が Msxml3.dll の読み込みに失敗した場合  
  
-   IDE が Mso.dll の読み込みに失敗した場合  
  
-   IDE が DTE.olb の読み込みに失敗した場合  
  
-   セットアップ時に Visual Studio のライセンス キーが作成されなかった場合  
  
-   スクリプト ブロックが有効になっているため、スクリプト コードを実行できなかった場合  
  
-   Visual Studio に必要なコンポーネントである .NET Framework のセットアップで、mscorlib.dll の有効なネイティブ イメージの生成に失敗した場合  
  
-   コンピューターが Klez ウイルスに感染している場合  
  
 このエラーを解決するには、次の手順に従ってください。  
  
> [!WARNING]
>  これらの解決方法には、レジストリ キーの編集が必要なものが含まれます。  レジストリ エディターで不適切な操作を行うと、重大な問題が発生して、オペレーティング システムの再インストールが必要になる場合もあります。  レジストリ エディターの不適切な使用によって生じた問題については、解決を保証できません。  問題が発生する可能性のあることを十分に認識したうえで利用してください。  
  
 IDE が Msxml3.dll の読み込みに失敗した場合  
 この状況は、2001 年 7 月リリースの MSXML 4.0 Technology Preview ベータ版で発生します。  Msxml3.dll の登録を修復するには、次の手順に従います。  
  
### Msxml4.dll のアンインストール  
  
1.  **\[スタート\]** ボタンをクリックし、**\[ファイル名を指定して実行\]** をクリックします。  
  
2.  **\[名前\]** ボックスに「`regsvr32 /u c:\winnt\system32\msxml4.dll`」と入力し、**\[OK\]** をクリックします。  
  
### MSXML のセキュリティ更新プログラムのダウンロードおよびインストール  
  
1.  コンピューターにインストールされているバージョンに対応する MSXML の最新のセキュリティ更新プログラムを、[http:\/\/www.microsoft.com\/windows\/ie\/downloads\/critical\/q317244\/download.asp](http://www.microsoft.com/windows/ie/downloads/critical/q317244/download.asp) からダウンロードします。  
  
2.  セキュリティ更新プログラムの .exe を実行します。  
  
### 更新されたレジストリ値のダウンロードおよび適用  
  
1.  更新したレジストリ値を [http:\/\/download.microsoft.com\/download\/VisualStudioNET\/fix\/1.0\/WIN98MeXP\/Fixxml4.exe](http://download.microsoft.com/download/VisualStudioNET/fix/1.0/WIN98MeXP/Fixxml4.exe) からダウンロードします。  
  
2.  fixxml4.exe をダブルクリックし、ファイルを解凍します。  
  
3.  Fixxml4.reg を探してダブルクリックすると、レジストリ値が更新されます。  
  
 IDE が Mso.dll の読み込みに失敗した場合  
 Mso.dll に関する問題を修復するには、次の操作を実行します。  
  
### Microsoft Office  
  
-   コンピューターから Microsoft Office XP ベータ版をアンインストールします。  
  
-   \[プログラムの追加と削除\] で Office XP を修復します。  
  
-   レジストリ エディターで、次のレジストリ キーを確認します。  
  
     `[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\7.0\Path] "MSO"="C:\Program Files\Common Files\Microsoft Shared\Office10\MSO.DLL"`  
  
 IDE が DTE.olb の読み込みに失敗した場合  
 このエラーを解決するには  
  
### Dte.olb の登録  
  
1.  **\[スタート\]** ボタンをクリックし、**\[ファイル名を指定して実行\]** をクリックします。  
  
2.  **\[名前\]** ボックスに「`regsvr32 C:\Program Files\Common Files\Microsoft Shared\MSEnv\DTE.OLB`」と入力し、**\[OK\]** をクリックします。  
  
 セットアップ時に Visual Studio のライセンス キーが作成されなかった場合  
 Visual Studio のスプラッシュ スクリーンに、インストールされている製品の一覧と、製品をインストールしたユーザーの情報が表示されなかった場合、ライセンス キーが欠落しています。  また、\[プログラムの追加と削除\] ダイアログ ボックスに Visual Studio が表示されていない場合も、ライセンス キーが欠落しています。  
  
 この問題を解決するには、次の手順に従います。  
  
### Visual Studio のライセンス キーの生成  
  
-   コンピューターから Visual Studio を完全に削除し、製品を再インストールします。  
  
 スクリプト ブロックが有効になっているため、スクリプト コードを実行できなかった場合  
 サードパーティのアプリケーションで、スクリプト ブロック機能が有効になっている場合、IDE がいったん表示された後で見えなくなります。  
  
-   この問題を解決するには、スクリプト ブロック機能が適切に機能していることを確認します。  
  
 Visual Studio に必要なコンポーネントである .NET Framework のセットアップで、mscorlib.dll の有効なネイティブ イメージの生成に失敗した場合  
 Visual Studio のスプラッシュ スクリーンが表示され、すぐに見えなくなる場合、Mscorlib.dll ファイルの有効なネイティブ イメージが欠落している可能性があります。  このファイルは、.NET Framework のセットアップ時に \\%windir%\\assembly\\NativeImages1\_v1.0.3705\\mscorlib ディレクトリに作成されます。  
  
 この問題を解決するには  
  
### 有効な Mscorlib.dll ファイルの作成  
  
1.  .NET Framework をアンインストールしてから、再インストールします。  
  
 コンピューターが Klez ウイルスに感染している場合  
 コンピューターが Klez ウイルスに感染していると、"アプリケーションを起動できません。" というエラーが表示されます。  ウイルス対策ソフトウェアを更新し、コンピューターをスキャンして、ウイルスに感染していないかどうかを確認してください。