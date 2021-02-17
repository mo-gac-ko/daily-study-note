## 📆 2월 17일 공부 기록

> MERN stack youtube 클론코딩 프로젝트 :)

    구독자들의 영상만 볼 수 있는 subscriptionPage 구현 완료
    비디오디테일페이지 내의 댓글 컴포넌트 생성 완료
    비디오디테일페이지 하단에 댓글영역 레이아웃 완료
    댓글 기능 구현을 위한 준비단계까지 완료

<br />

### Comment 스키마

```javascript
const mongoose = require("mongoose");

const Schema = mongoose.Schema;

const commentSchema = mongoose.Schema(
  {
    writer: {
      type: Schema.Types.ObjectId,
      ref: "User",
    },
    postId: {
      type: Schema.Types.ObjectId,
      ref: "Video",
    },
    responseTo: {
      type: Schema.Types.ObjectId,
      ref: "User",
    },
    content: {
      type: String,
    },
  },

  { timestamps: true }
);

const Comment = mongoose.model("Comment", commentSchema);

module.exports = { Comment };
```

<br />

### Comment 관련 api

```javascript
const express = require("express");
const router = express.Router();

const { Comment } = require("../models/Comment");

//=================================
//             Comment
//=================================

router.post("/saveComment", (req, res) => {
  const comment = new Comment(req.body);

  comment.save((err, comment) => {
    if (err) return res.json({ success: false, err });

    Comment.find({ _id: comment._id })
      .populate("writer")
      .exec((err, result) => {
        if (err) return res.json({ success: false, err });
        res.status(200).json({ success: true, result });
      });
  });
});
module.exports = router;
```

### Comment 컴포넌트

```Javascript
import Axios from "axios";
import React, { useEffect, useState } from "react";

import { useSelector } from "react-redux";

function Comment(props) {
  const videoId = props.postId;

  //redux state에서 값 가져오기
  const user = useSelector((state) => state.user);

  const [commentValue, setCommentValue] = useState("");

  const handleClick = (event) => {
    setCommentValue(event.currentTarget.value);
  };

  const onSubmit = (event) => {
    event.preventDefault();

    const variables = {
      content: commentValue,
      writer: user.userData._id,
      postId: videoId,
    };

    Axios.post("/api/comment/saveComment", variables).then((response) => {
      if (response.data.success) {
        console.log(response.data.result);
      } else {
        alert("코멘트를 저장하지 못했습니다.");
      }
    });
  };

  return (
    <div>
      <br />
      <p> Replies</p>
      <hr />
      {/* Comment Lists */}

      {/* Root Comment Form */}

      <form style={{ display: "flex" }} onSubmit={onSubmit}>
        <textarea
          style={{ width: "100%", borderRadius: "5px" }}
          onChange={handleClick}
          value={commentValue}
          placeholder="코멘트를 작성해 주세요"
        ></textarea>

        <br />
        <button style={{ width: "20%", height: "52px" }} onClick={onSubmit}>
          Submit
        </button>
      </form>
    </div>
  );
}

export default Comment;
```
