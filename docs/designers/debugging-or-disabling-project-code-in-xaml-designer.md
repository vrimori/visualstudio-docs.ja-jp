---
title: "XAML デザイナーでプロジェクト コードをデバッグまたは無効化する | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ac600581-8fc8-49e3-abdf-1569a3483d74
caps.latest.revision: 5
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 138f318b84044a1ed8a92f9b2ee7b47b2211cdb7
ms.lasthandoff: 02/22/2017

---
# <a name="debugging-or-disabling-project-code-in-xaml-designer"></a>XAML デザイナーでプロジェクト コードをデバッグまたは無効化する
ハンドルされない例外が XAML デザイナーで起こる原因の多くは、プロジェクト コードがアクセスしようとするプロパティまたはメソッドが、デザイナーでアプリケーションを実行するときに、返す値や動作方法が変わることにあります。 Visual Studio の別のインスタンスでプロジェクト コードをデバッグしてこれらの例外を解決するか、デザイナーでプロジェクトのコードを無効にして、一時的に例外を回避することができます。  
  
 プロジェクト コードには次のものが含まれます。  
  
-   カスタム コントロールおよびユーザー コントロール  
  
-   クラス ライブラリ  
  
-   値コンバーター  
  
-   プロジェクト コードから生成されるデザイン時のデータに対するバインド  
  
 プロジェクト コードが無効になると、Visual Studio は、たとえば、データが使用できなくなったバインドのプロパティ名などのプレースホルダーや、実行されなくなったコントロールのプレースホルダーを表示します。  
  
 ![ハンドルされない例外のダイアログ](~/designers/media/xaml_unhandledexception.png "XAML_UnhandledException")  
  
#### <a name="to-determine-if-project-code-is-causing-an-exception"></a>プロジェクト コードが例外の原因かどうかを判断するには  
  
1.  ハンドルされない例外のダイアログで、 **[ここをクリックして、デザイナーを再読み込み]** リンクを選びます。  
  
2.  メニュー バーで、 **[デバッグ]**、 **[デバッグ開始]** を選んでアプリケーションを実行します。  
  
     アプリケーションがビルドされ、正常に実行される場合は、デザイナーで実行されているプロジェクト コードによってデザイン時例外が発生する可能性があります。  
  
#### <a name="to-debug-project-code-running-in-the-designer"></a>デザイナーで実行されているプロジェクト コードをデバッグするには  
  
1.  ハンドルされない例外のダイアログで、 **[ここをクリックしてプロジェクト コードの実行を無効にし、デザイナーを再読み込み]** リンクを選びます。  
  
2.  Windows タスク マネージャーで、 **[タスクの終了]** ボタンを選び、現在実行している Visual Studio XAML デザイナーのすべてのインスタンスを閉じます。  
  
     ![TaskManager の XAML デザイナー インスタンス](~/designers/media/xaml_taskmanager.png "XAML_TaskManager")  
  
3.  Visual Studio で、デバッグするコードまたはコントロールを含む XAML ページを開きます。  
  
4.  Visual Studio の新しいインスタンスを開き、プロジェクトの&2; 番目のインスタンスを開きます。  
  
5.  プロジェクト コードにブレークポイントを設定します。  
  
6.  Visual Studio の新しいインスタンスのメニュー バーで、 **[デバッグ]**、 **[プロセスにアタッチ]**を選びます。  
  
7.  **[プロセスにアタッチ]** ダイアログの **[選択可能なプロセス]** 一覧で、 **XDesProc.exe**を選び、 **[アタッチ]** ボタンを選びます。  
  
     ![XAML デザイナー プロセス](~/designers/media/xaml_attach.png "XAML_Attach")  
  
     これは、Visual Studio の最初のインスタンスの XAML デザイナーの手順です。  
  
8.  Visual Studio の最初のインスタンスのメニュー バーで、 **[デバッグ]**、 **[デバッグ開始]**を選びます。  
  
     デザイナーで実行しているコードにステップ インできます。  
  
#### <a name="to-disable-project-code-in-the-designer"></a>デザイナーでプロジェクト コードを無効にするには  
  
-   ハンドルされない例外のダイアログで、 **[ここをクリックしてプロジェクト コードの実行を無効にし、デザイナーを再読み込み]** リンクを選びます。  
  
-   あるいは、XAML デザイナーのツール バーで、 **[プロジェクト コードを無効にする]** ボタンを選びます。  
  
     ![[プロジェクト コードの無効化] ボタン](~/designers/media/xaml_disablecode.png "XAML_DisableCode")  
  
     もう一度ボタンを切り替えて、プロジェクト コードを再び有効にできます。  
  
    > [!NOTE]
    >  ARM または X64 プロセッサがターゲットのプロジェクトの場合、Visual Studio は、デザイナーでプロジェクト コードを実行できないため、デザイナーで **[プロジェクト コードを無効にする]** ボタンは無効です。  
  
-   どちらかのオプションを実行するとデザイナーは再度読み込み、関連付けられているプロジェクトのすべてのコードを無効にします。  
  
    > [!NOTE]
    >  プロジェクト コードを無効にすると、デザイン時データが失われることがあります。 別の方法は、デザイナーで実行されているコードをデバッグすることです。  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio および Blend for Visual Studio での XAML の設計](../designers/designing-xaml-in-visual-studio.md)
