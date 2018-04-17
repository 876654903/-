<template>
    <div class="boardidea-page">
        <div class="title">广告创意</div>
        <div class="small-title">落地页</div>
        <div class="address">
            <span>着陆页地址：</span>
            <input type="text" placeholder="请设置广告名称">
            <span>预览</span>
        </div>
        <div class="small-title sendidea">上传创意</div>
        <div>
            创意一
        </div>

        <div class="addImg">
            <el-upload class="avatar-uploader" action="http://localhost:9999/dsp-creative/creative/upload" :show-file-list="false" :on-success="handleAvatarSuccess" :before-upload="beforeAvatarUpload">
                <img v-if="imageUrl" :src="imageUrl" class="avatar">
                <i v-else class="el-icon-plus avatar-uploader-icon"></i>
            </el-upload>
        </div>

    </div>
</template>
<script>
export default {
    data() {
        return {
            activeName: 'second',
             imageUrl: ''

        }
    },

     methods: {
      handleAvatarSuccess(res, file) {
         this.imageUrl = 'http://localhost:9999/'+res.data.value;
      },
      beforeAvatarUpload(file) {
        const isJPG = file.type === 'image/jpeg';
        const isLt2M = file.size / 1024 / 1024 < 2;

        if (!isJPG) {
          this.$message.error('上传头像图片只能是 JPG 格式!');
        }
        if (!isLt2M) {
          this.$message.error('上传头像图片大小不能超过 2MB!');
        }
        return isJPG && isLt2M;
      }
    }
}
</script>
<style lang="less" scoped>
.title {
    width: 206px;
    height: 45px;
    font-family: MicrosoftYaHei;
    font-size: 34px;
    color: rgba(0, 0, 0, 0.85);
    letter-spacing: 0;
    margin-top: 48px;
    margin-left: 24px;
}

.small-title {
    height: 26px;
    margin-top: 32px;
    margin-left: 24px;
    font-family: MicrosoftYaHei-Bold;
    font-size: 20px;
    color: rgba(0, 0, 0, 0.85);
    letter-spacing: 0;
    font-weight: bold;
}

.address {
    margin-top: 16px;
    margin-left: 24px;
    input {
        width: 432px;
        height: 32px;
        margin-left: 8px;
        padding-left: 10px;
        box-sizing: border-box;
    }
    >&:nth-child(1) {
        margin-left: 6px;
    }
    >&:nth-child(3) {
        margin-left: 6px;
    }
}

.sendidea {
    margin-top: 61px;
}


.button {
    padding-left: 24px;
}


 .avatar-uploader .el-upload {
    border: 1px dashed #d9d9d9;
    border-radius: 6px;
    cursor: pointer;
    position: relative;
    overflow: hidden;
    border:1px solid #ccc;
  }
  .avatar-uploader .el-upload:hover {
    border-color: #409EFF;
  }
  .avatar-uploader-icon {
    margin-top:24px;
    font-size: 28px;
    color: #8c939d;
    width: 178px;
    height: 178px;
    line-height: 178px;
    text-align: center;
    border:1px solid #ccc;
  }
  .avatar {
    width: 178px;
    height: 178px;
    border:1px solid #ccc;
    display: block;
  }

  .addImg{
      margin-left:24px; 
  }
</style>


