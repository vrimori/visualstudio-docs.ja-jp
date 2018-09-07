---
title: COM、VSTO、および VBA の office アドインの開発のベスト プラクティスします。
ms.custom: ''
ms.date: 07/25/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- ''
helpviewer_keywords:
- ''
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: bf00afb612e12ce6712206808897a3b851d68b3a
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/06/2018
ms.locfileid: "35671862"
---
# <a name="development-best-practices-for-com-vsto-and-vba-add-ins-in-office"></a>COM、VSTO、および VBA の office アドインの開発のベスト プラクティスします。
  Office の COM、VSTO または VBA アドインを開発する場合はこの記事で説明されている開発のベスト プラクティスに従います。   ことができます。

-  独自のアドインに Office の展開と異なるバージョン間での互換性。
-  ユーザーと IT 管理者の追加で展開の複雑さが軽減されます。
-  アドインのインストールまたは実行時の意図しないエラーが発生しません。

>注: を使用して、[デスクトップ ブリッジ](/windows/uwp/porting/desktop-to-uwp-root)COM を準備する VSTO または VBA アドインを Windows ストアがサポートされていません。 COM、VSTO と VBA アドインは、Windows ストアまたは Office ストアで配布することはできません。 
  
## <a name="do-not-check-for-office-during-installation"></a>Office のインストール中にオンにしないでください。  
 アドインのインストール プロセス中に Office がインストールされているかどうかを検出アドインもお勧めしません。 Office がインストールされていない場合、アドインをインストールすることができ、ユーザーが Office をインストールした後にアクセスできます。 
  
## <a name="use-embedded-interop-types-nopia"></a>埋め込まれた相互運用機能型 (NoPIA) の使用  
ソリューションが .NET 4.0 を使用して、または以降では、埋め込まれた相互運用機能型 (NoPIA) の代わりにに応じて、Office プライマリ相互運用機能アセンブリ (PIA) 再頒布可能パッケージ。 型の埋め込みを使用して、ソリューションのインストール サイズを縮小し、将来の互換性を確保します。 Office 2010 は、PIA 再頒布可能パッケージに同梱されている Office の最終バージョンでした。 詳細については、次を参照してください。[チュートリアル: Microsoft Office アセンブリから埋め込み型情報](https://msdn.microsoft.com/library/ee317478.aspx)と[等価性と埋め込まれた相互運用機能型の入力](/windows/uwp/porting/desktop-to-uwp-root)します。

ソリューションは、以前のバージョンの .NET を使用している場合は、.NET 4.0 以降を使用するソリューションを更新することをお勧めします。 .NET 4.0 以降を使用して、新しいバージョンの Windows での実行時の前提条件が軽減されます。
  
## <a name="avoid-depending-on-specific-office-versions"></a>特定の Office バージョンに応じて回避します。  
ソリューションにのみ新しいバージョンの Office で使用できる機能を使用する場合は、(たとえば、処理、または、バージョンを確認して例外を使用して) 実行時に、機能が (可能であれば、機能レベル) に存在するを確認します。 など、オブジェクト モデルでサポートされている Api を使用して、特定のバージョンではなく、最小バージョンは、検証、 [Application.Version プロパティ](https://msdn.microsoft.com/library/office/microsoft.office.interop.excel._application.version.aspx)します。 インストール、環境、およびバージョンとの間を変更できるため、Office バイナリ メタデータ、インストール パス、またはレジストリ キーに依存することをお勧めします。

## <a name="enable-both-32-bit-and-64-bit-office-usage"></a>Office の使用状況を 32 ビットと 64 ビットの両方を有効にします。   
既定の build ターゲットは、ソリューションは、特定のビット数でのみ使用するライブラリに依存していない限り 32 ビット (x86) と 64 ビット (x64) の両方をサポートする必要があります。 Office の 64 ビット版は特にビッグ データ環境での導入に増加します。 32 ビットと 64 ビットの両方のサポートやすく、ユーザーが Office の 32 ビットおよび 64 ビットのバージョン間の遷移です。

VBA コードを記述するとき使用して 64 ビットの安全は declare ステートメントし、適切な変数を変換します。 さらに、各ビット数のコードを提供することで、32 ビットまたは 64 ビット バージョンの Office を実行しているユーザーの間でドキュメントを共有できることを確認します。 詳細については、次を参照してください。 [64 ビットの Visual Basic アプリケーションの概要の](https://msdn.microsoft.com/library/office/gg264421.aspx)します。

## <a name="support-restricted-environments"></a>制限された環境をサポートします。   
ソリューションでは、ユーザー アカウントの昇格または管理者特権は必要ありません必要があります。 さらに、設定または変更するのには、ソリューションが依存する必要があります。

- 現在の作業ディレクトリ。
- DLL は、ディレクトリを読み込みます。
- PATH 変数。

## <a name="change-the-save-location-of-shared-data-and-settings"></a>変更の保存データの共有と設定の場所
ソリューション アドインと Office の外部にあるプロセスの場合、使用しないでください、ユーザーのアプリケーション データ フォルダーまたはレジストリ データや、アドインと外部のプロセス間の設定を交換します。 代わりに、ユーザーの一時フォルダー、ドキュメント フォルダー、またはソリューションのインストール ディレクトリを使用を検討してください。

## <a name="increment-the-version-number-with-each-update"></a>各更新プログラムのバージョン番号を増やす
ソリューション内のバイナリのバージョン番号を設定し、更新のたびにインクリメントします。 これは、ため、バージョン間の変更を特定し、互換性の評価をユーザーが簡単に、されます。

## <a name="provide-support-statements-for-the-latest-versions-of-office"></a>最新バージョンの Office のサポート ステートメントを提供します。
お客様は、COM、VSTO と VBA のアドインの Office で実行されるステートメントをサポートを提供する Isv を要求します。 Office 365 ProPlus を使用して、明示的なサポート ステートメントにより顧客の一覧を表示する準備ツールは、サポートを理解します。 

Office クライアント アプリケーション (Word、Excel など) のサポート ステートメントを提供するには、最初、アドインが Office の現在のリリースで実行してと将来のリリースに区切りが追加で更新プログラムを提供するためにコミットし、確認します。 Microsoft は、新しいビルドの場合、または Office の更新プログラムを離したときに、アドインをテストする必要はありません。 Microsoft Office では、COM、VSTO と VBA の拡張機能プラットフォームを変更頻度が低いと、これらの変更はも記載されています。

>重要: Microsoft では、対応状況レポート、および ISV の連絡先情報のサポート対象のアドインの一覧を保持します。 アドインを一覧表示を取得するを参照してください。 [ https://aka.ms/readyforwindows](https://aka.ms/readyforwindows)します。

## <a name="use-process-monitor-to-help-debug-installation-or-loading-issues"></a>インストールまたは読み込みの問題をデバッグする際に Process Monitor を使用します。
アドインをインストールまたは読み込み中に互換性の問題がある場合、は、ファイルまたはレジストリのアクセスに関する問題に関連があります。 使用[プロセス モニター](/sysinternals/downloads/procmon)または同様のデバッグ ツールにログインし、問題を特定する作業環境に対する動作を比較します。
