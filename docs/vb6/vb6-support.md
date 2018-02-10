---
title: "Visual Basic 6.0 のサポートについて |Microsoft ドキュメント"
ms.date: 08/28/2017
ms.technology: devlang-vb
ms.topic: article
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
ms.openlocfilehash: cb25f85be6c77dfbef6969435d14f2cae61debf2
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="support-statement-for-visual-basic-60-on-windows"></a>Visual Basic 6.0 を Windows のサポートについて


## <a name="executive-summary"></a>概要

Visual Basic チームは、次のサポートされている Windows オペレーティング システム上の Visual Basic 6.0 アプリケーション用の「だけ動作」互換性に努めています。 

- Windows 10
- Windows 8.1
- Windows 7
- Windows Server 2016
- Windows Server 2012 R2 を含む
- Windows Server 2008 R2 を含む

Visual Basic チームの目標は、Visual Basic 6.0 アプリケーションが引き続きサポートされているバージョンの Windows で実行することです。 このドキュメントで説明、コア Visual Basic 6.0 のランタイムに対してはサポート サポートされているバージョンの Windows の完全な lifetime は 5 年間の延長サポート (http://support.microsoft.com/gp/lifepolicy) の 5 年後にメイン ストリーム サポートします。 サポートのバーは重大な低下や既存のアプリケーションに関する重要なセキュリティの問題に制限されます。

## <a name="technical-summary"></a>技術概要

Visual Basic 6.0 は、これらのキーの成果物で構成されています。
- Visual Basic 6.0 IDE (統合開発環境) ではします。
- Visual Basic 6.0 のランタイム: 基本ライブラリと実行エンジンが VB 6.0 アプリケーションを実行するために使用します。
- Visual Basic 6.0 ランタイム拡張ファイル: 選択された ActiveX コントロールの .ocx ファイルのファイル、ライブラリ、および配布を IDE のメディアとオンライン版のツールです。

## <a name="the-visual-basic-60-ide"></a>Visual Basic 6.0 の IDE

Visual Basic 6.0 IDE は、2008 年 4 月 8 日の時点ではサポートされていません。 Windows および Visual Basic の両方のチームが Windows Vista、Windows 7、Windows Server 2008、Windows 8 および Windows 8.1 を理解し、(該当する場合) を軽減で Visual Basic 6.0 の IDE をテストするさらに、32 ビット バージョンの Windows (参照の互換性の問題[64 ビット Windows](#62-bit-windows) 64 ビット システムの詳細については、後述の「)。 このお知らせでは、IDE のサポート ポリシーは変更されません。

## <a name="the-visual-basic-60-runtime"></a>Visual Basic 6.0 のランタイム

Visual Basic 6.0 のランタイムは、もともと Visual Basic 6.0 の再頒布リストに含まれているコンパイル済みのバイナリ ファイルとして定義されます。 これらのファイルは、元の Visual Basic 6.0 のライセンスの再頒布可能としてマークされています。 これらのファイルの例として、Visual Basic 6.0 のランタイム ライブラリ (`msvbvm60.dll`)、コントロール (つまり、 `msflxgrd.ocx`) ランタイムと他の主要な機能領域 (つまり MDAC) のファイルをサポートします。

ランタイムは、3 つのグループに分かれています。

- サポートされているランタイム ファイル - オペレーティング システムで出荷

   大部分のアプリケーション シナリオで使用する、キー Visual Basic 6.0 のランタイム ファイルで出荷と、サポートされている Windows バージョンの有効期間はサポートされてです。 この有効期間は、5 年間のメイン ストリーム サポート、特定のバージョンの Windows に付属している時点から延長サポートの 5 つの年です。 サポートされているバージョンの Windows で実行されている Visual Basic 6.0 アプリケーションのテストの一部として互換性のため、これらのファイルがテスト済みです。 

   > [!NOTE]
   > サポートされているすべての Windows バージョンには、ファイルのとほぼ同じ一覧が含まれてし、これらのファイルを含むアプリケーションの再頒布可能パッケージの要件とほぼ同じにする必要があります。 1 つの主な違いは`TriEdit.dll`Windows Vista およびそれ以降のバージョンから削除されました。

- サポートされているランタイム ファイル:-アプリケーションを使用して配布するファイルの拡張

   この拡張の一覧は、主要な制御、ライブラリ、および IDE のメディアまたは Microsoft.com から開発者のコンピューターにインストールされているツールで構成されます。 通常、VB6 IDE は、既定では開発者のコンピューターにこれらのコントロールをインストールします。 開発者は、アプリケーションでこれらのファイルを再配布する必要があります。 サポートされているバージョンのファイルは、オンラインするには、Microsoft ダウンロード センター (http://go.microsoft.com/fwlink/?LinkID=142927) 利用可能です。

- サポートされていないランタイム ファイル

   メイン ストリーム外になったいずれかのいくつかのファイルがサポートまたはランタイムの再頒布可能パッケージの一部として含まれていたことはありません (に含まれていたなど、`\Tools`レガシの VB4/VB5 アプリケーションをサポートするために、IDE メディア上のフォルダーがサード パーティ製コントロールまたは)。 これらのファイルは Windows; でサポートされていませんそれらはどのようなサポート契約で出荷されたメディアに適用される可能性があります。 つまり、ありませんサポートやサービスに関して保証を一切いたしません。 場合によっては、これらのライブラリの以降のバージョンがサポートされます。 下位互換性やサポートされているバージョンへの移行の詳細を以下に示します。

各サポート グループに含まれるファイルの詳細を参照してください、[ランタイム定義](#runtime-definition)以下のセクションです。

## <a name="the-visual-basic-60-support-lifetime"></a>Visual Basic 6.0 のサポートの有効期間

サポートやサポートされているバージョンの Windows で Visual Basic 6.0 のランタイムのバイナリを配布は変更されませんサポート ポリシーの Visual Basic 6.0 IDE または Visual Studio 6.0 IDE 全体。 これらの製品は、2008 年 4 月 8 日で拡張サポートから移動します。

Microsoft 製品のサポート ライフ サイクルの詳細については、http://support.microsoft.com/gp/lifepolicy で確認できます。 、このサポート ライフ サイクルの一部として Microsoft は引き続きサポートされているバージョンの Windows でこれらのオペレーティング システムのサポートの有効期間にわたって Visual Basic 6.0 ランタイムをサポートします。 たとえば、Visual Basic 6.0 のランタイムがメイン ストリーム サポートについては、2008 年 6 月と拡張のサポートについては、2013 年 6 月まで Windows Server 2003 でサポートされていることを意味します。
サポート ライフ サイクルまたはその他のサポート オプションについての詳細については、http://www.microsoft.com/support にサポート ページにアクセスしてください。

## <a name="64-bit-windows"></a>64 ビット Windows

Visual Basic 6.0 のランタイム ファイルは、32 ビットです。 これらのファイルで 64 ビット Windows オペレーティング システムが次の表で参照されている付属しています。 32 ビット VB6 アプリケーションおよびコンポーネントは、WOW エミュレーション環境でのみサポートされます。 32 ビット コンポーネントは、32 ビット アプリケーション プロセスでホストすることも必要があります。

Visual Basic 6.0 の IDE は、ネイティブの 64 ビット バージョンで提供されることはありません。 また、32 ビット IDE サポートされている 64 ビット Windows で。 64 ビット Windows で 32 ビット以外のすべてのネイティブ アーキテクチャ VB6 開発し、サポートされていません。

## <a name="windows-7"></a>Windows 7

このサポート文書の最初のリリース以降、Windows 7 オペレーティング システムがリリースされました。 このドキュメントは、Windows 7 で VB6、Microsoft のサポートを明確に更新されました。

VB6 ランタイムでは、出荷および、OS の有効期間中に Windows 7 ではサポートされます。 Visual Basic 6.0 のランタイム ファイルは引き続きのみ、32 ビットになり、すべてのコンポーネントは、32 ビット アプリケーション プロセスでホストされる必要があります。

## <a name="windows-81"></a>Windows 8.1

このサポート文書の最初のリリース以降、Windows 8.1 オペレーティング システムがリリースされています。 このドキュメントは、Windows 8.1 における VB6 に対するマイクロソフトのサポートを明確に更新されました。

VB6 ランタイムでは、出荷および、OS の有効期間中に Windows 8.1 でサポートされます。 Visual Basic 6.0 のランタイム ファイルは引き続きのみ、32 ビットになり、すべてのコンポーネントは、32 ビット アプリケーション プロセスでホストされる必要があります。 開発者は、Windows 7 の場合と同じものとして Windows 8.1 のサポートのストーリーの考えることができます。

## <a name="windows-10"></a>Windows 10

このサポート文書の最初のリリース以降、Windows 10 オペレーティング システムがリリースされています。 このドキュメントは Windows 10 における VB6 に対するマイクロソフトのサポートを明確に更新されました。

VB6 ランタイムでは、出荷および、OS の有効期間中に Windows 10 でサポートされます。 Visual Basic 6.0 のランタイム ファイルは引き続きのみ、32 ビットになり、すべてのコンポーネントは、32 ビット アプリケーション プロセスでホストされる必要があります。 開発者は、Windows 8.1 の場合と同じものとして Windows 10 用のサポートのストーリーの考えることができます。

## <a name="windows-server-2008"></a>Windows Server 2008

このサポート文書の最初のリリース以降、Windows Server 2008 オペレーティング システムがリリースされています。 このドキュメントは、Windows Server 2008 における VB6 に対するマイクロソフトのサポートを明確に更新されました。

VB6 ランタイムでは、出荷および、OS の有効期間中に Windows Server 2008 ではサポートされます。 Visual Basic 6.0 のランタイム ファイルは引き続きのみ、32 ビットになり、すべてのコンポーネントは、32 ビット アプリケーション プロセスでホストされる必要があります。

## <a name="windows-server-2008-r2"></a>Windows Server 2008 R2

このサポート文書の最初のリリース以降、Windows Server 2008 R2 オペレーティング システムがリリースされています。 このドキュメントは、Windows Server 2008 R2 における VB6 に対するマイクロソフトのサポートを明確に更新されました。

VB6 ランタイムでは、出荷および、OS の有効期間中に Windows Server 2008 R2 でサポートされます。 Visual Basic 6.0 のランタイム ファイルは引き続きのみ、32 ビットになり、すべてのコンポーネントは、32 ビット アプリケーション プロセスでホストされる必要があります。 開発者は、Windows Server 2008 の場合と同じものとして Windows Server 2008 R2 のサポートのストーリーの考えることができます。

## <a name="windows-server-2012"></a>Windows Server 2012

このサポート文書の最初のリリース以降、Windows Server 2012 オペレーティング システムがリリースされています。 このドキュメントは、Windows Server 2012 における VB6 に対するマイクロソフトのサポートを明確に更新されました。

VB6 ランタイムでは、出荷および、OS の有効期間中に Windows Server 2012 でサポートされます。 Visual Basic 6.0 のランタイム ファイルは引き続きのみ、32 ビットになり、すべてのコンポーネントは、32 ビット アプリケーション プロセスでホストされる必要があります。 開発者は、Windows Server 2008 R2 の場合と同じものとして Windows Server 2012 のサポートのストーリーの考えることができます。

## <a name="windows-server-2012-r2"></a>Windows Server 2012 R2

このサポート文書の最初のリリース以降、Windows Server 2012 R2 オペレーティング システムがリリースされています。 このドキュメントは、Windows Server 2012 R2 における VB6 に対するマイクロソフトのサポートを明確に更新されました。

VB6 ランタイムでは、出荷および、OS の有効期間中に Windows Server 2012 R2 でサポートされます。 Visual Basic 6.0 のランタイム ファイルは引き続きのみ、32 ビットになり、すべてのコンポーネントは、32 ビット アプリケーション プロセスでホストされる必要があります。 開発者は、Windows Server 2012 の場合と同じものとして Windows Server 2012 R2 のサポートのストーリーの考えることができます。

## <a name="windows-server-2016"></a>Windows Server 2016

このサポート文書の最初のリリース以降、Windows Server 2016 のオペレーティング システムがリリースされています。 このドキュメントは、Windows Server 2016 における VB6 に対するマイクロソフトのサポートを明確に更新されました。

VB6 ランタイムでは、出荷および、OS の有効期間中に Windows Server 2016 ではサポートされます。 Visual Basic 6.0 のランタイム ファイルは引き続きのみ、32 ビットになり、すべてのコンポーネントは、32 ビット アプリケーション プロセスでホストされる必要があります。 開発者は、Windows Server 2012 R2 の場合と同じものとして Windows Server 2016 のサポートのストーリーの考えることができます。

## <a name="supported-windows-operating-system-versions"></a>サポートされている Windows オペレーティング システムのバージョン

このセクションでは、一定レベルの VB6 のサポートを提供するオペレーティング システムに関する追加情報を提供します。 

|Windows オペレーティング システム|サポートされているランタイムの VB6</br>Windows で出荷ファイルでは、サポートされているか。|VB6 Rutime のサポート</br>拡張ファイル</br>アプリケーションを使用して配布がサポートされているか。| VB6 IDE サポートを有無|
|---|---|---|---|
|Windows 10、すべての 32 ビット エディション|[はい] *|[はい] *|×|
|Windows 10、すべての 64 ビット エディション (WOW のみ)|[はい] * </br> のみの WOW で実行されている 32 ビット アプリ|はい* </br> のみの WOW で実行されている 32 ビット アプリ|×|
|Windows 8.1、すべての 32 ビット エディション|[はい] *|[はい] *|×|
| Windows 8.1、すべての 64 ビット エディション (WOW のみ)|[はい] * </br> のみの WOW で実行されている 32 ビット アプリ|はい* </br> のみの WOW で実行されている 32 ビット アプリ|×|
|Windows 7、すべての 32 ビット エディション|[はい] *|[はい] *|×|
|Windows 7、すべての 64 ビット エディション (WOW のみ)|[はい] * </br> のみの WOW で実行されている 32 ビット アプリ|[はい] * </br> のみの WOW で実行されている 32 ビット アプリ|×|
|Windows Server 2016、すべての 64 ビット エディション (WOW のみ)|はい* </br> のみの WOW で実行されている 32 ビット アプリ|はい* </br> のみの WOW で実行されている 32 ビット アプリ|×|
|Windows Server 2012 R2 のすべての 64 ビット エディション (WOW のみ)<br>Windows Server 2012 のすべての 64 ビット エディション (WOW のみ)|はい* </br> のみの WOW で実行されている 32 ビット アプリ|はい* </br> のみの WOW で実行されている 32 ビット アプリ|×|
|Windows Server 2008 R2 のすべての x64 エディション (WOW のみ)</br>Windows Server 2008 では、すべての x64 エディション (WOW のみ)|[はい] * </br> のみの WOW で実行されている 32 ビット アプリ|[はい] * </br> のみの WOW で実行されている 32 ビット アプリ|×|
|すべての 32 ビット エディション、Windows Server 2008|[はい] *|[はい] *|×|


> [!NOTE]
> &#42;です。 VB6 ランタイム サポートは、Windows のサポート ライフ サイクルによって制限されます。  たとえば、ターゲット OS は、延長サポートは、VB6 は延長サポートよりも高いレベルのサポートを持つことはできません。  [Windows サポート ライフ サイクル ファクト シート](https://support.microsoft.com/en-us/help/13853/windows-lifecycle-fact-sheet)現在と以前のバージョンの Windows の他のライフ サイクルについて説明します。

## <a name="visual-basic-60-runtime-usage-inside-vba-and-office"></a>VBA とオフィス内の Visual Basic 6.0 ランタイムの使用量

アプリケーション、または VBA、Visual Basic は、一般的にアプリケーションの自動化と Microsoft Office アプリケーション内で最もよく、他のアプリケーション内でのマクロの使用異なるテクノロジです。 Office の一部として同梱されて VBA と VBA のサポートが Office のサポート ポリシーによって管理されるためです。 ただし、呼び出しまたは Visual Basic 6.0 のランタイム バイナリおよびコントロールをホストする VBA が使用されている場合があります。 このような場合は、Visual Basic 6.0 の OS でサポートされているランタイムのファイルと、拡張ファイルの一覧は、サポートされている VBA 環境の内部で使用する場合にもサポートされています。

VB6 VBA 内にサポートするシナリオをランタイムでは、次のすべての必要があります。

- VB ランタイムのホスト OS のバージョンがサポートされてもします。
- Office VBA for のホストのバージョンがサポートされてもします。
- 該当するランタイム ファイルは引き続きサポートされます。

## <a name="visual-basic-script-vbscript"></a>Visual Basic スクリプト (VBScript)

VBScript では、Visual Basic 6.0 とサポート ステートメントに関係ありません。 ただし、VBScript では、Windows 7、Windows 8.1、Windows 10、Windows Server 2008 R2、Windows Server 2012 R2、および Windows Server 2016 を含むを含むの一部として現在出荷されており、OS のサポート ライフ サイクルによって拘束されます。

## <a name="third-party-components"></a>サード パーティのコンポーネント

マイクロソフトは、OCX/ActiveX コントロールなどのサード パーティのコンポーネントのサポートを提供することはできません。 お客様は、それらのコンポーネントのサポートの詳細について、元のコントロール販売元にお問い合わせください。

## <a name="reporting-issues-with-vb-60-applications-running-on-windows"></a>Windows で実行されている VB 6.0 アプリケーションとレポートに関する問題

表示されている Windows オペレーティング システムのいずれかの Visual Basic 6.0 を使用する計画開発者は、そのオペレーティング システムをインストールし、元のアプリケーションの検証テストを使用してアプリケーション互換性テストを開始します。

表示されている Windows オペレーティング システムのいずれかで実行されている Visual Basic 6.0 アプリケーションと共に問題を検出する場合は、問題を報告、通常のサポート チャネルに従ってください。

## <a name="supported-and-shipping-in-windows"></a>サポートされているしで出荷 Windows

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

## <a name="supported-runtime-files-to-distribute-with-your-application"></a>サポートされているランタイム ファイルをアプリケーションと共に配布するには

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

## <a name="unsupported-but-supported-and-compatible-updates-or-upgrades-are-available"></a>サポートされていない、サポートされていると互換性のある更新プログラムやアップグレードは使用できますが、

| | | | |
|---|---|---|---|
|dao350.dll|   msexch35.dll| msjter35.dll| msrepl35.dll|
|mdac_typ.exe| msexcl35.dll| msjtor35.dll| mstext35.dll|
|mschart.ocx|  msjet35.dll|  msltus35.dll| msxbse35.dll|
|msdaerr.dll|  msjint35.dll| mspdox35.dll| odbctl32.dll|
|msdatl2.dll|  msjt4jlt.dll| msrd2x35.dll| oledb32x.dll|

## <a name="unsupported-runtime-files"></a>サポートされていないランタイム ファイル

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

## <a name="localization-support-binaries"></a>ローカリゼーションをサポートするバイナリ

次のバイナリは、Windows オペレーティング システムのローカライズ版で実行されている Visual Basic 6.0 アプリケーションをサポートするために必要です。 サポートされますが、Windows に付属していません。 これらのファイルは、アプリケーションのセットアップと共に出荷する必要があります。

### <a name="supported-runtime-files-to-distribute-with-your-application"></a>サポートされているランタイム ファイルをアプリケーションと共に配布するには

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

