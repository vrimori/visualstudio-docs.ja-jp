---
title: "COM、VSTO、および VBA の office アドインの開発のベスト プラクティス |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/25/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: 
helpviewer_keywords: 
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 2a1b6b9270207b3d0f8d415655231af4456e61b4
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/10/2018
---
# <a name="development-best-practices-for-com-vsto-and-vba--add-ins-in-office"></a>COM、VSTO、および VBA のアドインの office 開発のベスト プラクティス
  Office 用に COM、VBA、または VSTO アドインを開発する場合はこの記事で説明する開発のベスト プラクティスに従います。   これによりすることができます。

-  独自のアドインに Office の展開と異なるバージョン間での互換性。
-  ユーザーと IT 管理者のアドインの配置の複雑さを軽減します。
-  アドインでの意図しないインストールまたは実行時エラーは発生しません。

>注: を使用して、[デスクトップ ブリッジ](/windows/uwp/porting/desktop-to-uwp-root)を使用している COM を準備するには、VSTO または VBA 用アドインに Windows ストアはサポートされていません。 COM、VSTO、および VBA アドインは、Windows ストアまたは Office ストアに分散できません。 
  
## <a name="do-not-check-for-office-during-installation"></a>インストール時に Office を確認しません。  
 追加で、アドインのインストール プロセス中に Office がインストールされているかどうかを検出することはお勧めしません。 Office がインストールされていない場合、アドインをインストールすることができ、ユーザーは Office のインストール後にアクセスすることにします。 
  
## <a name="use-embedded-interop-types-nopia"></a>埋め込まれた相互運用機能型 (NoPIA) を使用します。  
場合は、ソリューションが .NET 4.0 を使用して、または後で、使用して埋め込まれた相互運用機能型 (NoPIA) の代わりにに応じて、Office プライマリ相互運用機能アセンブリ (PIA) 再頒布可能パッケージ。 型の埋め込みを使用して、ソリューションのインストールのサイズを削減し、将来の互換性を確保します。 Office 2010 では、PIA の再頒布可能パッケージに同梱されている Office の最新バージョンをでした。 詳細については、次を参照してください。[チュートリアル: Microsoft Office アセンブリから型情報を埋め込む](https://msdn.microsoft.com/en-us/library/ee317478.aspx)と[型の等価性と埋め込まれた相互運用機能型](/windows/uwp/porting/desktop-to-uwp-root)です。

ソリューションは、以前のバージョンの .NET を使用している場合は、.NET 4.0 以降を使用するソリューションを更新することをお勧めします。 .NET 4.0 以降を使用するには、新しいバージョンの Windows で実行時の前提条件が少なくなります。
  
## <a name="avoid-depending-on-specific-office-versions"></a>特定のバージョンの Office によって回避します。  
ソリューションは、以降のバージョンで提供される機能を使用している場合は、(たとえば、例外処理や、バージョンを確認して、使用して) 実行時に (可能であれば、機能レベルで機能が存在することを確認します。 など、オブジェクト モデルでサポートされている Api を使用して、特定のバージョンではなく、最小バージョンは、検証、 [Application.Version プロパティ](https://msdn.microsoft.com/en-us/library/office/microsoft.office.interop.excel._application.version.aspx)です。 これらのインストール、環境、およびバージョンの間で変更できるため Office バイナリ メタデータ、インストール パス、またはレジストリ キーに依存することはお勧めしません。

## <a name="enable-both-32-bit-and-64-bit-office-usage"></a>Office の使用状況を 32 ビットおよび 64 ビットの両方を有効にします。   
既定の build ターゲットは、ソリューションは、特定のビット数でのみ使用されるライブラリに依存しない限り、32 ビット (x86) と 64 ビット (x64) の両方をサポートする必要があります。 Office の 64 ビット バージョンが導入実績、ビッグ データの環境で特に大きくなる状況です。 32 ビットおよび 64 ビットの両方をサポートしやすく、ユーザーが Office の 32 ビットおよび 64 ビット バージョンの間の遷移します。

VBA コードを記述する場合を使用して 64 ビットの安全がステートメントを宣言し、適切な変数を変換します。 また、各ビット数のコードを提供することによって、32 ビットまたは 64 ビット バージョンの Office を実行しているユーザーの間でドキュメントを共有できることを確認します。 詳細については、次を参照してください。 [64 ビットの Visual Basic アプリケーションの概要 for](https://msdn.microsoft.com/en-us/library/office/gg264421.aspx)です。

## <a name="support-restricted-environments"></a>制限された環境をサポートします。   
ソリューションでは、ユーザー アカウントの昇格または管理者の特権は必要ありません。 さらに、ソリューションは設定または変更することに依存しないようにします。

- 現在の作業ディレクトリです。
- DLL は、ディレクトリを読み込みます。
- パス変数です。

## <a name="change-the-save-location-of-shared-data-and-settings"></a>保存先を変更する共有データと設定の場所
ソリューションがの場合は、アドインと Office の外部にあるプロセス、使わないユーザーのアプリケーション データ フォルダーやレジストリ データや、アドインと外部のプロセス間で設定を交換します。 代わりに、ユーザーの一時フォルダー、ドキュメント フォルダー、または、ソリューションのインストール ディレクトリを使用します。

## <a name="increment-the-version-number-with-each-update"></a>各更新プログラムのバージョン番号を増やす
ソリューション内のバイナリのバージョン番号を設定し、更新のたびにインクリメントします。 これは、ため、バージョン間の変更を特定して互換性を評価ユーザーが簡単に、されます。

## <a name="provide-support-statements-for-the-latest-versions-of-office"></a>最新のバージョンの Office のサポートの説明を提供します。
お客様は、COM、VSTO、および VBA アドインを Office 内で実行のサポートの説明を提供する Isv を求めています。 Office 365 ProPlus を使用して、明示的なサポート ステートメントにより顧客の一覧を表示する準備ツールは、サポートを理解します。 

Office クライアント アプリケーション (Word や Excel など) のサポートの説明を提供するには、最初ことを確認、アドイン Office の現在のリリースで実行場合は、将来のリリースで改行を追加では、更新プログラムを提供することにコミットし。 新しいビルドの場合、または Office の更新プログラムをリリースするときに、独自のアドインをテストする必要はありません。 Microsoft Office では、COM、VSTO、および VBA extensibility プラットフォームはめったに変更して、これらの変更は、文書化します。

>重要: Microsoft は、サポートされているアドイン準備レポート、および ISV の連絡先情報の一覧を保持します。 アドインを一覧表示を参照してください[https://aka.ms/readyforwindows](https://aka.ms/readyforwindows)です。

## <a name="use-process-monitor-to-help-debug-installation-or-loading-issues"></a>プロセス モニターを使用してインストールまたは読み込みの問題をデバッグします。
アドインをインストールまたは読み込み中に互換性の問題がある場合、は、ファイルまたはレジストリのアクセスに関する問題に関連する可能性があります。 使用して[プロセス モニター](/sysinternals/downloads/procmon)または同様のデバッグ ツールをログに記録して問題を特定するための作業環境に対して動作を比較します。
