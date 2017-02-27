---
title: "メッセージの列挙子 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "メッセージの列挙子"
  - "ソース管理プラグインをメッセージの列挙"
ms.assetid: 4a4faa0d-d352-40ea-a21d-c09ea286a8e1
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# メッセージの列挙子
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

次のフラグを使用しての `TEXTOUTPROC` 関数を呼び出すときに IDE で提供するコールバック関数、 [SccOpenProject](../extensibility/sccopenproject-function.md) \(を参照してください [LPTEXTOUTPROC](../extensibility/lptextoutproc.md) 詳細については、コールバック関数で\)。  
  
 IDE の処理を取り消すことが確認された場合はそこはキャンセル メッセージのいずれかを取得することがあります。 ソースがプラグインで使用を管理する場合は、 `SCC_MSG_STARTCANCEL` を表示するための IDE を確認する、 **キャンセル** \] ボタンをクリックします。 その後、通常のメッセージのセットを送信できます。 これらの返される結果のいずれかの場合 `SCC_MSG_RTN_CANCEL`, 、プラグイン、操作を終了するし、返されます。 プラグインもポーリング `SCC_MSG_DOCANCEL` 定期的に更新して、ユーザーが操作の取り消しかどうかを判断します。 すべての操作が完了すると、またはユーザーがキャンセルされた場合、プラグインが送信時に `SCC_MSG_STOPCANCEL`します。`SCC_MSG_INFO`, 、SCC\_MSG\_WARNING、SCC\_MSG\_ERROR 型は、メッセージの一覧に表示されているメッセージに使用されます。`SCC_MSG_STATUS` ステータス バーまたは一時的な表示領域にテキストが表示されることを示す特殊な型です。 維持されない永続的に、一覧にします。  
  
## 構文  
  
```  
enum {   
   SCC_MSG_RTN_CANCEL = -1,   
   SCC_MSG_RTN_OK = 0,   
   SCC_MSG_INFO = 1   
   SCC_MSG_WARNING,   
   SCC_MSG_ERROR,   
   SCC_MSG_STATUS,   
   SCC_MSG_DOCANCEL,   
   SCC_MSG_STARTCANCEL,   
   SCC_MSG_STOPCANCEL   
};  
```  
  
## メンバー  
 SCC\_MSG\_RTN\_CANCEL  
 \[キャンセル\] を示すためにコールバックから戻る  
  
 SCC\_MSG\_RTN\_OK  
 コールバックを続行するかを返します。  
  
 SCC\_MSG\_INFO  
 情報メッセージです。  
  
 SCC\_MSG\_WARNING  
 メッセージは警告です。  
  
 SCC\_MSG\_ERROR  
 メッセージは、エラーです。  
  
 SCC\_MSG\_STATUS  
 ステータス バーのメッセージが用意されています。  
  
 SCC\_MSG\_DOCANCEL  
 テキストがないです。IDE が返す `SCC_MSG_RTN_OK` または `SCC_MSG_RTN_CANCEL`です。  
  
 SCC\_MSG\_STARTCANCEL  
 \[キャンセル\] ループを開始します。  
  
 SCC\_MSG\_STOPCANCEL  
 \[キャンセル\] ループを停止します。  
  
## 参照  
 [ソース管理プラグイン](../extensibility/source-control-plug-ins.md)   
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)