---
title: Visual Basic 6.0 のサポートに関する声明 | Microsoft Docs
ms.date: 08/28/2017
ms.technology: devlang-vb
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- VB6 support
- Visual Basic 6.0 support
ms.assetid: ffc5ba4d-44d7-4ef7-a3f6-38a8738bf127
author: paulyuk
ms.author: paulyuk
ms.workload:
- paulyuk
ms.openlocfilehash: cc55dec5960717e3807602bc76031f7502ec90c9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="support-statement-for-visual-basic-60-on-windows"></a>Windows 版 Visual Basic 6.0 のサポートに関する声明


## <a name="executive-summary"></a>概要

Visual Basic チームは、次のサポート対象の Windows オペレーティング システム上で、Visual Basic 6.0 アプリケーションが "問題なく動作する" ことに取り組んでいます。 

- Windows 10
- Windows 8.1
- Windows 7
- Windows Server 2016
- Windows Server 2012 (R2 を含む)
- Windows Server 2008 (R2 を含む)

Visual Basic チームの目標は、Visual Basic 6.0 アプリケーションがサポート対象の Windows バージョンで継続的に実行されるようにすることです。 フルの有効期間のサポートされている Windows バージョンでは、5 年間の延長サポートの 5 年後にメイン ストリーム サポートは、このドキュメントで詳しいとしてコア Visual Basic 6.0 のランタイムがサポートされます (http://support.microsoft.com/gp/lifepolicy)です。 サポート バーは、既存のアプリケーションに関する深刻な機能後退や致命的なセキュリティの問題に限定されます。

## <a name="technical-summary"></a>技術概要

Visual Basic 6.0 は、主に次の内容で構成されています。
- Visual Basic 6.0 IDE (統合開発環境)。
- Visual Basic 6.0 ランタイム: VB 6.0 アプリケーションの実行に使用される基本ライブラリと実行エンジン。
- Visual Basic 6.0 ランタイム拡張ファイル: IDE メディアに付属およびオンライン リリースで配布される、指定の ActiveX コントロール OCX ファイル、ライブラリ、およびツール。

## <a name="the-visual-basic-60-ide"></a>Visual Basic 6.0 IDE

Visual Basic 6.0 IDE のサポートは 2008 年 4 月 8 日をもって終了しています。 さらに、Windows の 32 ビット バージョンにおける互換性の問題について理解および軽減 (適切な場合) するために、Windows チームと Visual Basic チームが Visual Basic 6.0 IDE を Windows Vista、Windows 7、Windows Server 2008、Windows 8、および Windows 8.1 でテストしました (64 ビット システムの詳細情報については、以下の「[64 ビット版 Windows](#62-bit-windows)」のセクションを参照してください)。 このお知らせにより、IDE のサポート ポリシーが変更されることはありません。

## <a name="the-visual-basic-60-runtime"></a>Visual Basic 6.0 ランタイム

Visual Basic 6.0 ランタイムは、もともとは Visual Basic 6.0 の再頒布リストに含まれていたコンパイル済みのバイナリ ファイルとして定義されています。 これらのファイルは、オリジナルの Visual Basic 6.0 のライセンスで再頒布可能としてマークされています。 これらのファイルの例として、Visual Basic 6.0 ランタイム ライブラリ (`msvbvm60.dll`)、コントロール (`msflxgrd.ocx`)、他の主な機能領域 (MDAC) のランタイム サポート ファイルなどがあります。

ランタイムは、次の 3 つのグループに分かれています。

- サポート対象のランタイム ファイル - OS に付属

   主な Visual Basic 6.0 ランタイム ファイル。大部分のアプリケーション シナリオで使用されており、サポート対象の Windows バージョンに付属し、全有効期間にわたってサポートされます。 有効期間は、5 年間のメインストリーム サポートと 5 年間の拡張サポートで、そのバージョンの Windows が出荷された時点から始まります。 これらのファイルは、サポート対象の Windows バージョンで実行される Visual Basic 6.0 アプリケーションのテストの一環として、互換性がテストされています。 

   > [!NOTE]
   > サポート対象のすべての Windows バージョンに含まれているファイルの一覧はほぼ同じであり、これらのファイルが含まれるアプリケーションの再頒布要件はほぼ同じにする必要があります。 主な違いとしては、Windows Vista 以降のバージョンからは `TriEdit.dll` が削除されています。

- サポート対象のランタイム ファイル: アプリケーションで配布する拡張ファイル

   この拡張リストは、IDE メディアまたは Microsoft.com から開発者のマシンにインストールされた、主なコントロール、ライブラリ、ツールで構成されます。 通常、これらのコントロールは VB6 IDE によって開発者のコンピューターに既定でインストールされます。 開発者は引き続きアプリケーションでこれらのファイルを再配布する必要があります。 サポートされているバージョンのファイルは使用可能なオンラインには、Microsoft ダウンロード センター (http://go.microsoft.com/fwlink/?LinkID=142927)です。

- サポート対象外のランタイム ファイル

   一部のファイルはメインストリーム サポートの対象外となったか、元からランタイム再頒布可能ファイルの一部として含まれていませんでした (たとえば、レガシーの VB4/VB5 アプリケーションをサポートするために IDE メディアの `\Tools` フォルダーに含まれていた、またはサードパーティのコントロールであったなど)。 これらのファイルは Windows ではサポートされません。それらが付属するメディアに適用されるサポート契約に従います。 これは、サポートとサービスに関する保証はないことを意味します。 場合によっては、これら以降のバージョンのライブラリがサポートされます。 下位互換性やサポート対象のバージョンへの移行の詳細については、以下を参照してください。

各サポート グループに含まれるファイルの詳細については、以下の[ランタイム定義](#runtime-definition)に関するセクションを参照してください。

## <a name="the-visual-basic-60-support-lifetime"></a>Visual Basic 6.0 のサポートの有効期間

Visual Basic 6.0 ランタイム バイナリがサポート対象の Windows バージョンでサポートされるまたは付属することにより、Visual Basic 6.0 IDE や Visual Studio 6.0 IDE 全体としてのサポート ポリシーが変わることはありません。 これらの製品の拡張サポートは、2008 年 4 月 8 日をもって終了しています。

Microsoft 製品のサポート ライフ サイクルの詳細についてはありますhttp://support.microsoft.com/gp/lifepolicyです。 サポート有効期間の一部として、マイクロソフトはサポート対象の Windows バージョン上の Visual Basic 6.0 ランタイムについて、そのオペレーティング システムのサポート有効期間にわたって、引き続きサポートします。 つまり、たとえば Windows Server 2003 上のVisual Basic 6.0 ランタイムについては、メインストリーム サポートは 2008 年 6 月まで、拡張サポートについては 2013 年 6 月まで提供します。
サポート ライフ サイクルまたはその他のサポート オプションについての詳細がサポート ページをご参照くださいhttp://www.microsoft.com/supportです。

## <a name="64-bit-windows"></a>64 ビット版 Windows

Visual Basic 6.0 ランタイム ファイルは 32 ビットです。 これらのファイルは、以下の表に示す 64 ビット版の Windows オペレーティング システムに付属します。 32 ビットの VB6 アプリケーションとコンポーネントは、WOW エミュレーション環境でのみサポートされます。 また、32 ビットのコンポーネントは 32 ビット アプリケーション プロセスにホストされている必要があります。

Visual Basic 6.0 IDE は、ネイティブの 64 ビット バージョンで提供されることはありません。また、32 ビット版の IDE は 64 ビット版の Windows でサポートされません。 64 ビット版の Windows および 32 ビット以外の他のネイティブなアーキテクチャでの VB6 の開発はサポートされておらず、今後もサポートされません。

## <a name="windows-7"></a>Windows 7

Window 7 オペレーティング システムは、このサポートに関する声明の初期リリース後にリリースされました。 このドキュメントは、マイクロソフトの Windows 7 での VB6 のサポートを明確にするように更新されました。

VB6 ランタイムは Windows 7 に付属し、その OS の有効期間にわたってサポートされます。 Visual Basic 6.0 ランタイム ファイルは引き続き 32 ビット版のみで、すべてのコンポーネントは 32 ビット アプリケーション プロセスでホストされる必要があります。

## <a name="windows-81"></a>Windows 8.1

Window 8.1 オペレーティング システムは、このサポートに関する声明の初期リリース後にリリースされました。 このドキュメントは、マイクロソフトの Windows 8.1 での VB6 のサポートを明確にするように更新されました。

VB6 ランタイムは Windows 8.1 に付属し、その OS の有効期間にわたってサポートされます。 Visual Basic 6.0 ランタイム ファイルは引き続き 32 ビット版のみで、すべてのコンポーネントは 32 ビット アプリケーション プロセスでホストされる必要があります。 開発者は Windows 8.1 におけるサポートの内容は Windows 7 と同じであると捉えて問題ありません。

## <a name="windows-10"></a>Windows 10

Window 10 オペレーティング システムは、このサポートに関する声明の初期リリース後にリリースされました。 このドキュメントは、マイクロソフトの Windows 10 での VB6 のサポートを明確にするように更新されました。

VB6 ランタイムは Windows 10 に付属し、その OS の有効期間にわたってサポートされます。 Visual Basic 6.0 ランタイム ファイルは引き続き 32 ビット版のみで、すべてのコンポーネントは 32 ビット アプリケーション プロセスでホストされる必要があります。 開発者は Windows 10 におけるサポートの内容は Windows 8.1 と同じであると捉えて問題ありません。

## <a name="windows-server-2008"></a>Windows Server 2008

Window Server 2008 オペレーティング システムは、このサポートに関する声明の初期リリース後にリリースされました。 このドキュメントは、マイクロソフトの Windows Server 2008 での VB6 のサポートを明確にするように更新されました。

VB6 ランタイムは Windows Server 2008 に付属し、その OS の有効期間にわたってサポートされます。 Visual Basic 6.0 ランタイム ファイルは引き続き 32 ビット版のみで、すべてのコンポーネントは 32 ビット アプリケーション プロセスでホストされる必要があります。

## <a name="windows-server-2008-r2"></a>Windows Server 2008 R2

Windows Server 2008 R2 オペレーティング システムは、このサポートに関する声明の初期リリース後にリリースされました。 このドキュメントは、マイクロソフトの Windows Server 2008 R2 での VB6 のサポートを明確にするように更新されました。

VB6 ランタイムは Windows Server 2008 R2 に付属し、その OS の有効期間にわたってサポートされます。 Visual Basic 6.0 ランタイム ファイルは引き続き 32 ビット版のみで、すべてのコンポーネントは 32 ビット アプリケーション プロセスでホストされる必要があります。 開発者は Windows Server 2008 R2 におけるサポートの内容は Windows Server 2008 と同じであると捉えて問題ありません。

## <a name="windows-server-2012"></a>Windows Server 2012

Windows Server 2012 オペレーティング システムは、このサポートに関する声明の初期リリース後にリリースされました。 このドキュメントは、マイクロソフトの Windows Server 2012 での VB6 のサポートを明確にするように更新されました。

VB6 ランタイムは Windows Server 2012 に付属し、その OS の有効期間にわたってサポートされます。 Visual Basic 6.0 ランタイム ファイルは引き続き 32 ビット版のみで、すべてのコンポーネントは 32 ビット アプリケーション プロセスでホストされる必要があります。 開発者は Windows Server 2012 におけるサポートの内容は Windows Server 2008 R2 と同じであると捉えて問題ありません。

## <a name="windows-server-2012-r2"></a>Windows Server 2012 R2

Windows Server 2012 R2 オペレーティング システムは、このサポートに関する声明の初期リリース後にリリースされました。 このドキュメントは、マイクロソフトの Windows Server 2012 R2 での VB6 のサポートを明確にするように更新されました。

VB6 ランタイムは Windows Server 2012 R2 に付属し、その OS の有効期間にわたってサポートされます。 Visual Basic 6.0 ランタイム ファイルは引き続き 32 ビット版のみで、すべてのコンポーネントは 32 ビット アプリケーション プロセスでホストされる必要があります。 開発者は Windows Server 2012 R2 におけるサポートの内容は Windows Server 2012 と同じであると捉えて問題ありません。

## <a name="windows-server-2016"></a>Windows Server 2016

Windows Server 2016 オペレーティング システムは、このサポートに関する声明の初期リリース後にリリースされました。 このドキュメントは、マイクロソフトの Windows Server 2016 での VB6 のサポートを明確にするように更新されました。

VB6 ランタイムは Windows Server 2016 に付属し、その OS の有効期間にわたってサポートされます。 Visual Basic 6.0 ランタイム ファイルは引き続き 32 ビット版のみで、すべてのコンポーネントは 32 ビット アプリケーション プロセスでホストされる必要があります。 開発者は Windows Server 2016 におけるサポートの内容は Windows Server 2012 R2 と同じであると捉えて問題ありません。

## <a name="supported-windows-operating-system-versions"></a>サポート対象の Windows オペレーティング システムのバージョン

このセクションでは、一定のレベルで VB6 をサポートするオペレーティング システムに関する追加情報を提供します。 

|Windows オペレーティング システム|Windows に付属する VB6 で</br>サポートされるランタイム ファイルのサポート|アプリケーションで配布する VB6 で</br>サポートされる</br>ランタイム拡張ファイルのサポート| VB6 IDE のサポート|
|---|---|---|---|
|Windows 10、すべての 32 ビット エディション|あり*|あり*|×|
|Windows 10、すべての 64 ビット エディション (WOW のみ)|あり* </br> WOW のみで実行される 32 ビット アプリ|はい* </br> WOW のみで実行される 32 ビット アプリ|×|
|Windows 8.1、すべての 32 ビット エディション|あり*|あり*|×|
| Windows 8.1、すべての 64 ビット エディション (WOW のみ)|あり* </br> WOW のみで実行される 32 ビット アプリ|はい* </br> WOW のみで実行される 32 ビット アプリ|×|
|Windows 7、すべての 32 ビット エディション|あり*|あり*|×|
|Windows 7、すべての 64 ビット エディション (WOW のみ)|あり* </br> WOW のみで実行される 32 ビット アプリ|あり* </br> WOW のみで実行される 32 ビット アプリ|×|
|Windows Server 2016、すべての 64 ビット エディション (WOW のみ)|はい* </br> WOW のみで実行される 32 ビット アプリ|はい* </br> WOW のみで実行される 32 ビット アプリ|×|
|Windows Server 2012 R2、すべての 64 ビット エディション (WOW のみ)<br>Windows Server 2012、すべての 64 ビット エディション (WOW のみ)|はい* </br> WOW のみで実行される 32 ビット アプリ|はい* </br> WOW のみで実行される 32 ビット アプリ|×|
|Windows Server 2008 R2、すべての x64 エディション (WOW のみ)</br>Windows Server 2008、すべての x64 エディション (WOW のみ)|あり* </br> WOW のみで実行される 32 ビット アプリ|あり* </br> WOW のみで実行される 32 ビット アプリ|×|
|Windows Server 2008、すべての 32 ビット エディション|あり*|あり*|×|


> [!NOTE]
> &#42;  VB6 ランタイムのサポートは、Windows のサポート有効期間によって制限されます。  たとえば、対象の OS が拡張サポート期間に入っている場合、VB6 でそれより高いレベルのサポートを受けることはできません。  [Windows サポート有効期間ファクト シート](https://support.microsoft.com/en-us/help/13853/windows-lifecycle-fact-sheet)には、過去および現行の Windows バージョンの有効期間に関する追加情報が記載されています。

## <a name="visual-basic-60-runtime-usage-inside-vba-and-office"></a>VBA および Office 内での Visual Basic 6.0 ランタイムの使用状況

VBA (Visual Basic for Applications) は、アプリケーションの自動化のために他のアプリケーション (主に Microsoft Office アプリケーション) 内のマクロで一般的に使用される、別個のテクノロジーです。 VBA は Office の一部として付属し、そのため VBA のサポートは Office のサポート ポリシーに帰属します。 ただし、Visual Basic 6.0 ランタイムのバイナリやコントロールの呼び出しやホストに、VBA が使用される場合があります。 このような状況下で、サポート対象の VBA 環境内で使用されるときは、OS でサポートされる Visual Basic 6.0 のランタイム ファイルや拡張ファイルのリストもサポートされます。

VB6 ランタイム シナリオが VBA 内でサポートされるには、次のすべてが満たされている必要があります。

- VB ランタイムをホストする OS のバージョンが引き続きサポートされている。
- VBA の Office のホスト バージョンが引き続きサポートされている。
- 対象のランタイム ファイルが引き続きサポートされている。

## <a name="visual-basic-script-vbscript"></a>Visual Basic Script (VBScript)

VBScript は Visual Basic 6.0 とは関連性がなく、このサポートに関する声明は適用されません。 ただし、VBScript は現在、Windows 7、Windows 8.1、Windows 10＜Windows Server 2008 (R2 を含む)、Windows Server 2012 (R2 を含む) および Windows Server 2016 に付属しており、OS のサポート有効期間に帰属します。

## <a name="third-party-components"></a>サードパーティのコンポーネント

マイクロソフトは、OCX/ActiveX コントロールなどのサードパーティのコンポーネントに対してサポートを提供することはできません。 これらのコンポーネントのサポートの詳細については、販売元にお問い合わせください。

## <a name="reporting-issues-with-vb-60-applications-running-on-windows"></a>Windows で実行されている VB 6.0 アプリケーションに関する問題の報告

ここに挙げられている Windows オペレーティング システムのいずれかで Visual Basic 6.0 を使用することを計画している開発者は、そのオペレーティング システムをインストールして、元のアプリケーション承認テストを使用してアプリケーションの互換性テストを開始してください。

ここに挙げられているいずれかの Windows オペレーティング システムにおいて、Visual Basic 6.0 アプリケーションの実行で問題が見つかった場合は、通常のサポート チャネルに問題を報告してください。

## <a name="supported-and-shipping-in-windows"></a>サポート対象かつ Windows に付属

| | | | |
|---|---|---|---|
|atl.dll|         msadcor.dll|     msorcl32.dll|   ole2.dll|
|asycfilt.dll|    msadcs.dll|      msvbvm60.dll|   ole32.dll|
|comcat.dll|      msadds.dll|      msvcirt.dll|    oleaut32.dll|
|compobj.dll|     msaddsr.dll|     msvcrt.dll|     oleaut32.dll|
|dbnmpntw.dll|    msader15.dll|    msvcrt40.dll|   oledb32.dll|
|dcomcnfg.exe|    msado15.dll|     mtxdm.dll|      oledb32r.dll|
|dllhost.exe|     msador15.dll|    mtxoci.dll|     oledlg.dll|
|ds16gt.dll|      msadrh15.dll|    odbc16gt.dll|   olepro32.dll|
|ds32gt.dll|      mscpxl32.dll|    odbc32.dll|     olethk32.dll|
|expsrv.dll|      msdadc.dll|      odbc32gt.dll|   regsvr32.exe|
|hh.exe|          msdaenum.dll|    odbcad32.exe|   rpcns4.dll|
|hhctrl.ocx|      msdaer.dll|      odbccp32.cpl|   rpcrt4.dll|
|imagehlp.dll|    msdaora.dll|     odbccp32.dll|   scrrun.dll|
|iprop.dll|       msdaosp.dll|     odbccr32.dll|   secur32.dll|
|itircl.dll|      msdaprst.dll|    odbccu32.dll|   simpdata.tlb|
|itss.dll|        msdaps.dll|      odbcint.dll|    sqloledb.dll|
|mfc40.dll|       msdasc.dll|      odbcji32.dll|   sqlsrv32.dll|
|mfc42.dll|       msdasql.dll|     odbcjt32.dll|   stdole2.tlb|
|mfc42enu.dll|    msdasqlr.dll|    odbctrac.dll|   stdole32.tlb|
|msadce.dll|      msdatsrc.tlb|    oddbse32.dll|   storage.dll|
|msadcer.dll|     msdatt.dll|      odexl32.dll|    vbajet32.dll|
|msadcf.dll|      msdfmap.dll|     odfox32.dll|    vfpodbc.dll|
|msadcfr.dll|     msdfmap.ini|     odpdx32.dll|                |
|msadco.dll|      msjtes40.dll|    odtext32.dll|               |

## <a name="supported-runtime-files-to-distribute-with-your-application"></a>アプリケーションで配布するサポート対象のランタイム ファイル

| | | | |
|---|---|---|---|
|comct232.ocx |msbind.dll   |msdbrptr.dll  |msstdfmt.dll| 
|comct332.ocx |mscdrun.dll  |msflxgrd.ocx  |msstkprp.dll| 
|comctl32.ocx |mschrt20.ocx |mshflxgd.ocx  |mswcrun.dll|  
|comdlg32.ocx |mscomct2.ocx |mshtmpgr.dll  |mswinsck.ocx| 
|dbadapt.dll  |mscomctl.ocx |msinet.ocx    |picclp32.ocx| 
|dbgrid32.ocx |mscomm32.ocx |msmapi32.ocx  |richtx32.ocx| 
|dblist32.ocx |msdatgrd.ocx |msmask32.ocx  |sysinfo.ocx|  
|mci32.ocx    |msdatlst.ocx |msrdc20.ocx   |tabctl32.ocx| 
|msadodc.ocx  |msdatrep.ocx |msrdo20.dll

## <a name="unsupported-but-supported-and-compatible-updates-or-upgrades-are-available"></a>サポート対象外、ただしサポート対象および互換性のある更新またはアップグレードあり

| | | | |
|---|---|---|---|
|dao350.dll|   msexch35.dll| msjter35.dll| msrepl35.dll|
|mdac_typ.exe| msexcl35.dll| msjtor35.dll| mstext35.dll|
|mschart.ocx|  msjet35.dll|  msltus35.dll| msxbse35.dll|
|msdaerr.dll|  msjint35.dll| mspdox35.dll| odbctl32.dll|
|msdatl2.dll|  msjt4jlt.dll| msrd2x35.dll| oledb32x.dll|

## <a name="unsupported-runtime-files"></a>サポート対象外のランタイム ファイル

| | | | |
|---|---|---|---|
|anibtn32.ocx| spin32.ocx|   rpcltscm.dll|  rdocurs.dll|
|graph32.ocx|  gauge32.ocx|  rpcmqcl.dll|   vbar332.dll|
|keysta32.ocx| gswdll32.dll| rpcmqsvr.dll|  visdata.exe|
|autmgr32.exe| ciscnfg.exe|  rpcss.exe|     vsdbflex.srg|
|autprx32.dll| olecnv32.dll| dbmsshrn.dll|  threed32.ocx|
|racmgr32.exe| rpcltc1.dll|  dbmssocn.dll|  MSWLess.ocx|
|racreg32.dll| rpcltc5.dll|  windbver.exe|  tlbinf32.dll|
|grid32.ocx|   rpcltccm.dll| msderun.dll|   triedit.dll|
|msoutl32.ocx| rpclts5.dll|  odkob32.dll|

## <a name="localization-support-binaries"></a>ローカライズ サポート バイナリ

次のバイナリは、Windows オペレーティング システムのローカライズ版で実行されている Visual Basic 6.0 アプリケーションをサポートするために必要です。 サポート対象ですが、Windows には付属していません。 これらのファイルは、アプリケーションのセットアップで配布する必要があります。

### <a name="supported-runtime-files-to-distribute-with-your-application"></a>アプリケーションで配布するサポート対象のランタイム ファイル

|JPN|KOR|CHT|CHS|
|---|---|---|---|
|mfc42jpn.dll|  mfc42kor.dll|  mfc42cht.dll|  mfc42chs.dll|
|scrrnjp.dll|   scrrnko.dll|   scrrncht.dll|  scrrnchs.dll|
|vb6jp.dll|     vb6ko.dll|     vb6cht.dll|    vb6chs.dll|
|cmct2jp.dll|   cmct2ko.dll|   cmct2cht.dll|  cmct2chs.dll|
|cmct3jp.dll|   cmct3ko.dll|   cmct3cht.dll|  mscc2chs.dll|
|mscc2jp.dll|   mscc2ko.dll|   mscc2cht.dll|  cmct3chs.dll|
|cmctljp.dll|   cmctlko.dll|   cmctlcht.dll|  cmctlchs.dll|
|cmdlgjp.dll|   cmdlgko.dll|   mscmccht.dll|  mscmcchs.dll|
|mscmcjp.dll|   mscmcko.dll|   cmdlgcht.dll|  cmdlgchs.dll|
|dbgrdjp.dll|   dbgrdko.dll|   dbgrdcht.dll|  dbgrdchs.dll|
|dblstjp.dll|   dblstko.dll|   dblstcht.dll|  dblstchs.dll|
|mcijp.dll|     mciko.dll|     mcicht.dll|    mcichs.dll|
|msadnjp.dll|   msadnko.dll|   msadncht.dll|  msadnchs.dll|
|adodcjp.dll|   adodcko.dll|   adodccht.dll|  adodcchs.dll|
|mschtjp.dll|   mschtko.dll|   mschtcht.dll|  mschtchs.dll|
|msch2jp.dll|   msch2ko.dll|   msch2cht.dll|  msch2chs.dll|
|mscomjp.dll|   mscomko.dll|   mscomcht.dll|  mscomchs.dll|
|datgdjp.dll|   datgdko.dll|   datgdcht.dll|  datgdchs.dll|
|datlsjp.dll|   datlsko.dll|   datlscht.dll|  datlschs.dll|
|datrpjp.dll|   datrpko.dll|   datrpcht.dll|  datrpchs.dll|
|dbrprjp.dll|   dbrprko.dll|   dbrprcht.dll|  dbrprchs.dll|
|flxgdjp.dll|   flxgdko.dll|   flxgdcht.dll|  flxgdchs.dll|
|mshfgjpn.dll|  mshfgkor.dll|  mshfgcht.dll|  mshfgchs.dll|
|htmprjp.dll|   htmprko.dll|   htmprcht.dll|  htmprchs.dll|
|inetjp.dll|    inetko.dll|    inetcht.dll|   inetchs.dll|
|msmpijp.dll|   msmpiko.dll|   msmpicht.dll|  msmpichs.dll|
|msmskjp.dll|   msmskko.dll|   msmskcht.dll|  msmskchs.dll|
|rdc20jp.dll|   rdc20ko.dll|   rdc20cht.dll|  rdc20chs.dll|
|rdo20jp.dll|   rdo20ko.dll|   rdo20cht.dll|  rdo20chs.dll|
|stdftjp.dll|   stdftko.dll|   stdftcht.dll|  stdftchs.dll|
|mswcrjp.dll|   mswcrko.dll|   mswcrcht.dll|  mswcrchs.dll|
|winskjp.dll|   winskko.dll|   winskcht.dll|  winskchs.dll|
|pcclpjp.dll|   pcclpko.dll|   pcclpcht.dll|  pcclpchs.dll|
|rchtxjp.dll|   rchtxko.dll|   rchtxcht.dll|  rchtxchs.dll|
|sysinjp.dll|   sysinko.dll|   sysincht.dll|  sysinchs.dll|
|tabctjp.dll|   tabctko.dll|   tabctcht.dll|  tabctchs.dll|

|ITA|FRA|ESP|DEU|
|---|---|---|---|
|mfc42ita.dll|  mfc42fra.dll|  mfc42esp.dll|  mfc42deu.dll|
|scrrnit.dll|   scrrnfr.dll|   scrrnes.dll|   scrrnde.dll|
|vb6it.dll|     vb6fr.dll|     vb6es.dll|     vb6de.dll|
|cmct2it.dll|   cmct2fr.dll|   cmct2es.dll|   cmct2de.dll|
|mscc2it.dll|   mscc2fr.dll|   mscc2es.dll|   mscc2de.dll|
|cmct3it.dll|   cmct3fr.dll|   cmct3es.dll|   cmct3de.dll|
|cmctlit.dll|   cmctlfr.dll|   cmctles.dll|   cmctlde.dll|
|mscmcit.dll|   mscmcfr.dll|   mscmces.dll|   mscmcde.dll|
|cmdlgit.dll|   cmdlgfr.dll|   cmdlges.dll|   cmdlgde.dll|
|dbgrdit.dll|   dbgrdfr.dll|   dbgrdes.dll|   dbgrdde.dll|
|dblstit.dll|   dblstfr.dll|   dblstes.dll|   dblstde.dll|
|mciit.dll|     mcifr.dll|     mcies.dll|     mcide.dll|
|msadnit.dll|   msadnfr.dll|   msadnes.dll|   msadnde.dll|
|adodcit.dll|   adodcfr.dll|   adodces.dll|   adodcde.dll|
|mschtit.dll|   mschtfr.dll|   mschtes.dll|   mschtde.dll|
|msch2it.dll|   msch2fr.dll|   msch2es.dll|   msch2de.dll|
|mscomit.dll|   mscomfr.dll|   mscomes.dll|   mscomde.dll|
|atgdit.dll|    datgdfr.dll|   datgdes.dll|   datgdde.dll|
|datlsit.dll|   datlsfr.dll|   datlses.dll|   datlsde.dll|
|datrpit.dll|   datrpfr.dll|   datrpes.dll|   datrpde.dll|
|dbrprit.dll|   dbrprfr.dll|   dbrpres.dll|   dbrprde.dll|
|flxgdit.dll|   flxgdfr.dll|   flxgdes.dll|   flxgdde.dll|
|mshfgit.dll|   mshfgfr.dll|   mshfges.dll|   mshfgde.dll|
|htmprit.dll|   htmprfr.dll|   htmpres.dll|   htmprde.dll|
|inetit.dll|    inetfr.dll|    inetes.dll|    inetde.dll|
|msmpiit.dll|   msmpifr.dll|   msmpies.dll|   msmpide.dll|
|msmskit.dll|   msmskfr.dll|   msmskes.dll|   msmskde.dll|
|rdc20it.dll|   rdc20fr.dll|   rdc20es.dll|   rdc20de.dll|
|rdo20it.dll|   rdo20fr.dll|   rdo20es.dll|   rdo20de.dll|
|stdftit.dll|   stdftfr.dll|   stdftes.dll|   stdftde.dll|
|mswcrit.dll|   mswcrfr.dll|   mswcres.dll|   mswcrde.dll|
|winskit.dll|   winskfr.dll|   winskes.dll|   winskde.dll|
|pcclpit.dll|   pcclpfr.dll|   pcclpes.dll|   pcclpde.dll|
|rchtxit.dll|   rchtxfr.dll|   rchtxes.dll|   rchtxde.dll|
|sysinit.dll|   sysinfr.dll|   sysines.dll|   sysinde.dll|
|tabctit.dll|   tabctfr.dll|   tabctes.dll|   tabctde.dll|

