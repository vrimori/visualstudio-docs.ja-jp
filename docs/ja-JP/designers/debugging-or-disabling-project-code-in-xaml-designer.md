---
title: XAML デザイナーでプロジェクト コードをデバッグまたは無効化する
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: ac600581-8fc8-49e3-abdf-1569a3483d74
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: 9d77aa1d776352edd3a030507bc25086cad47d58
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="debug-or-disable-project-code-in-xaml-designer"></a>XAML デザイナーでプロジェクト コードをデバッグまたは無効化する

ハンドルされない例外が XAML デザイナーで起こる原因の多くは、プロジェクト コードがアクセスしようとするプロパティまたはメソッドが、デザイナーでアプリケーションを実行するときに、返す値や動作方法が変わることにあります。 Visual Studio の別のインスタンスでプロジェクト コードをデバッグしてこれらの例外を解決するか、デザイナーでプロジェクトのコードを無効にして、一時的に例外を回避することができます。

プロジェクト コードには次のものが含まれます。

-   カスタム コントロールおよびユーザー コントロール

-   クラス ライブラリ

-   値コンバーター

-   プロジェクト コードから生成されるデザイン時のデータに対するバインド

プロジェクト コードが無効になると、Visual Studio によってプレースホルダーが表示されます。 たとえば、データが使用できなくなったバインドのプロパティ名などのプレースホルダーや、実行されなくなったコントロールのプレースホルダーが表示されます。

![[ハンドルされていない例外] ダイアログ](../designers/media/xaml_unhandledexception.png)

## <a name="to-determine-if-project-code-is-causing-an-exception"></a>プロジェクト コードが例外の原因かどうかを判断するには

1.  ハンドルされない例外のダイアログで、 **[ここをクリックして、デザイナーを再読み込み]** リンクを選びます。

2.  メニュー バーで、**[デバッグ]** > **[デバッグ開始]** の順に選択して、アプリケーションを実行します。

     アプリケーションがビルドされ、正常に実行される場合は、デザイナーで実行されているプロジェクト コードによってデザイン時例外が発生する可能性があります。

## <a name="to-debug-project-code-running-in-the-designer"></a>デザイナーで実行されているプロジェクト コードをデバッグするには

1.  ハンドルされない例外のダイアログで、 **[ここをクリックしてプロジェクト コードの実行を無効にし、デザイナーを再読み込み]** リンクを選びます。

2.  Windows タスク マネージャーで、 **[タスクの終了]** ボタンを選び、現在実行している Visual Studio XAML デザイナーのすべてのインスタンスを閉じます。

     ![TaskManager の XAML デザイナー インスタンス](../designers/media/xaml_taskmanager.png)

3.  Visual Studio で、デバッグするコードまたはコントロールを含む XAML ページを開きます。

4.  Visual Studio の新しいインスタンスを開き、プロジェクトの 2 番目のインスタンスを開きます。

5.  プロジェクト コードにブレークポイントを設定します。

6.  Visual Studio の新しいインスタンスのメニュー バーで、**[デバッグ]** > **[プロセスにアタッチ]** の順に選択します。

7.  **[プロセスにアタッチ]** ダイアログの **[選択可能なプロセス]** 一覧で、 **XDesProc.exe**を選び、 **[アタッチ]** ボタンを選びます。

     ![XAML デザイナー プロセス](../designers/media/xaml_attach.png)

     これは、Visual Studio の最初のインスタンスの XAML デザイナーの手順です。

8.  Visual Studio の最初のインスタンスのメニュー バーで、**[デバッグ]** > **[デバッグ開始]** の順に選択します。

     デザイナーで実行しているコードにステップ インできます。

## <a name="to-disable-project-code-in-the-designer"></a>デザイナーでプロジェクト コードを無効にするには

-   ハンドルされない例外のダイアログで、 **[ここをクリックしてプロジェクト コードの実行を無効にし、デザイナーを再読み込み]** リンクを選びます。

-   あるいは、XAML デザイナーのツール バーで、 **[プロジェクト コードを無効にする]** ボタンを選びます。

     ![[プロジェクト コードの無効化] ボタン](../designers/media/xaml_disablecode.png)

     もう一度ボタンを切り替えて、プロジェクト コードを再び有効にできます。

    > [!NOTE]
    > ARM または X64 プロセッサがターゲットのプロジェクトの場合、Visual Studio は、デザイナーでプロジェクト コードを実行できないため、デザイナーで **[プロジェクト コードを無効にする]** ボタンは無効です。

-   どちらかのオプションを実行するとデザイナーは再度読み込み、関連付けられているプロジェクトのすべてのコードを無効にします。

    > [!NOTE]
    > プロジェクト コードを無効にすると、デザイン時データが失われることがあります。 別の方法は、デザイナーで実行されているコードをデバッグすることです。

## <a name="see-also"></a>関連項目

- [Visual Studio および Blend for Visual Studio での XAML の設計](../designers/designing-xaml-in-visual-studio.md)